![Screenshot from 2023-02-19 11-04-17](https://user-images.githubusercontent.com/115702866/219928048-b9d25fe6-c847-4df9-a43e-0359055f373b.png)

First I ran the program using the given command in my terminal.
```terminal
youguess@youguess-Inspiron-14-5410-2-in-1:~$ nc jupiter.challenges.picoctf.org 8311


                                                                             
                          #                mmmmm  mmmmm    "    mm   m   mmm 
  mmm    mmm    mmm    mmm#          mmm   #   "# #   "# mmm    #"m  # m"   "
 #   "  #"  #  #"  #  #" "#         #   "  #mmm#" #mmmm"   #    # #m # #   mm
  """m  #""""  #""""  #   #          """m  #      #   "m   #    #  # # #    #
 "mmm"  "#mm"  "#mm"  "#m##         "mmm"  #      #    " mm#mm  #   ##  "mmm"
                                                                             


Welcome! The game is easy: you jump on a sPRiNG.
How high will you fly?

LEVEL (1/30)

Guess the height: 8
WRONG! Sorry, better luck next time!
^Z
[1]+  Stopped                 nc jupiter.challenges.picoctf.org 8311
```

Entering a random height yielded no result. In order to acquire the flag we have to guess the right height 30 times in a row.
Using a decompiler i obtained the following source code for the program.

```c
undefined4 main(undefined1 param_1)
{
  uint local_20;
  uint local_1c;
  uint local_18;
  int local_14;
  undefined1 *local_10;
  
  local_10 = &param_1;
  puts("");
  puts("");
  puts("                                                                             ");
  puts("                          #                mmmmm  mmmmm    \"    mm   m   mmm ");
  puts("  mmm    mmm    mmm    mmm#          mmm   #   \"# #   \"# mmm    #\"m  # m\"   \"");
  puts(" #   \"  #\"  #  #\"  #  #\" \"#         #   \"  #mmm#\" #mmmm\"   #    # #m # #   mm");
  puts(
      "  \"\"\"m  #\"\"\"\"  #\"\"\"\"  #   #          \"\"\"m  #      #   \"m   #    #  # # #    #"
      );
  puts(" \"mmm\"  \"#mm\"  \"#mm\"  \"#m##         \"mmm\"  #      #    \" mm#mm  #   ##  \"mmm\"");
  puts("                                                                             ");
  puts("");
  puts("");
  puts("Welcome! The game is easy: you jump on a sPRiNG.");
  puts("How high will you fly?");
  puts("");
  fflush(stdout);
  local_18 = time((time_t *)0x0);
  srand(local_18);
  local_14 = 1;
  while( true ) {
    if (0x1e < local_14) {
      puts("Congratulation! You\'ve won! Here is your flag:\n");
      get_flag();
      fflush(stdout);
      return 0;
    }
    printf("LEVEL (%d/30)\n",local_14);
    puts("");
    local_1c = rand();
    local_1c = local_1c & 0xf;
    printf("Guess the height: ");
    fflush(stdout);
    __isoc99_scanf(&DAT_00010c9a,&local_20);
    fflush(stdin);
    if (local_1c != local_20) break;
    local_14 = local_14 + 1;
  }
  puts("WRONG! Sorry, better luck next time!");
  fflush(stdout);
                    /* WARNING: Subroutine does not return */
  exit(-1);
}
```

The srand() function is basically a random number generator that generates a random number using the current time.
(PRNG {Pseudo Random Number Generator} is capitalized in challenge name)
We need to create another program with the function srant(time(0)) that runs at the same time as the original program to provide us with the
required output that matches the original program.

```c
#include <stdio.h> 
#include <time.h>
#include <stdlib.h> 
  
int main () 
{ 
    int i;
      
    srand(time(0)); 
    
    for (i = 0; i < 30; i++)
    {
        printf("%d\n", rand() & 0xf); 
    }
      
    return 0; 
}
```

We run this program on the server in order to match the times.

```terminal
youguess@youguess-Inspiron-14-5410-2-in-1:~$ ./solve | nc jupiter.challenges.picoctf.org 8311


                                                                             
                          #                mmmmm  mmmmm    "    mm   m   mmm 
  mmm    mmm    mmm    mmm#          mmm   #   "# #   "# mmm    #"m  # m"   "
 #   "  #"  #  #"  #  #" "#         #   "  #mmm#" #mmmm"   #    # #m # #   mm
  """m  #""""  #""""  #   #          """m  #      #   "m   #    #  # # #    #
 "mmm"  "#mm"  "#mm"  "#m##         "mmm"  #      #    " mm#mm  #   ##  "mmm"
                                                                             


Welcome! The game is easy: you jump on a sPRiNG.
How high will you fly?

LEVEL (1/30)

Guess the height: LEVEL (2/30)

Guess the height: LEVEL (3/30)

Guess the height: LEVEL (4/30)

Guess the height: LEVEL (5/30)

Guess the height: LEVEL (6/30)

Guess the height: LEVEL (7/30)

Guess the height: LEVEL (8/30)

Guess the height: LEVEL (9/30)

Guess the height: LEVEL (10/30)

Guess the height: LEVEL (11/30)

Guess the height: LEVEL (12/30)

Guess the height: LEVEL (13/30)

Guess the height: LEVEL (14/30)

Guess the height: LEVEL (15/30)

Guess the height: LEVEL (16/30)

Guess the height: LEVEL (17/30)

Guess the height: LEVEL (18/30)

Guess the height: LEVEL (19/30)

Guess the height: LEVEL (20/30)

Guess the height: LEVEL (21/30)

Guess the height: LEVEL (22/30)

Guess the height: LEVEL (23/30)

Guess the height: LEVEL (24/30)

Guess the height: LEVEL (25/30)

Guess the height: LEVEL (26/30)

Guess the height: LEVEL (27/30)

Guess the height: LEVEL (28/30)

Guess the height: LEVEL (29/30)

Guess the height: LEVEL (30/30)

Guess the height: Congratulation! You've won! Here is your flag:

picoCTF{pseudo_random_number_generator_not_so_random_248ec303}
```

On running the programs simultaneously we obtain the flag:picoCTF{pseudo_random_number_generator_not_so_random_248ec303}



