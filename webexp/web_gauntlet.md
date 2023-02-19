# Description

![0](https://user-images.githubusercontent.com/125740625/219954067-774e0000-2e13-4b84-ba8c-808a05e561b4.png)

# Solution

Opening the links, I saw ..

![1](https://user-images.githubusercontent.com/125740625/219954162-a71c51c9-091c-46cb-b569-762f551ea0cc.png)        ![2](https://user-images.githubusercontent.com/125740625/219954172-74e868ba-f667-467c-92fe-b9e31235b52b.png)

I tried using credentials 'admin' and 'pass'

![4](https://user-images.githubusercontent.com/125740625/219954497-ae62601c-8e4f-44cf-a4a3-2133bd3278ea.png)

We get following error. So, there must be some script that is checking if username is 'admin' AND some password. We know by the hints this challenge has something to with SQL so I tried putting username 
```
admin' /* 
```
to comment the rest and random password.

![2](https://user-images.githubusercontent.com/125740625/219954675-cfb26ede-559b-430a-a68e-2e88de3243bd.png)

We are in Round 2/5 now, I tried repeating the same username ...

We are in Round 3/5 now, I tried repeating the same username... still on Round 3.

filler.php shows
```
Round3: or and = like > < --
```

I tried to search around on web and saw that we can use semi colon to end statement in code and thereby bypassing password. So I tried username:
```
admin';
```
We are in Round 4/5 now, I tried repeating the same username ... Nope.

filler.php shows
```
Round4: or and = like > < -- admin
```
We aren't allowed to use word admin. Only way we not type admin and still send back admin can be by sending it in parts...and then concatenating..

![5](https://user-images.githubusercontent.com/125740625/219955284-52447a1b-be79-4606-9b18-d218b6d0c9d7.png)

So I input username 
```
a'||'dmin';
```
with random password.

We are in Round 5/5 now, I tried repeating the same username ...filler.php shows
```
Round5: or and = like > < -- union admin
```
We are in Round 6/5 now, filler.php shows
```
 <?php
session_start();

if (!isset($_SESSION["round"])) {
    $_SESSION["round"] = 1;
}
$round = $_SESSION["round"];
$filter = array("");
$view = ($_SERVER["PHP_SELF"] == "/filter.php");

if ($round === 1) {
    $filter = array("or");
    if ($view) {
        echo "Round1: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 2) {
    $filter = array("or", "and", "like", "=", "--");
    if ($view) {
        echo "Round2: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 3) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--");
    // $filter = array("or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round3: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 4) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--", "admin");
    // $filter = array(" ", "/**/", "--", "or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round4: ".implode(" ", $filter)."<br/>";
    }
} else if ($round === 5) {
    $filter = array(" ", "or", "and", "=", "like", ">", "<", "--", "union", "admin");
    // $filter = array("0", "unhex", "char", "/*", "*/", "--", "or", "and", "=", "like", "union", "select", "insert", "delete", "if", "else", "true", "false", "admin");
    if ($view) {
        echo "Round5: ".implode(" ", $filter)."<br/>";
    }
} else if ($round >= 6) {
    if ($view) {
        highlight_file("filter.php");
    }
} else {
    $_SESSION["round"] = 1;
}

// picoCTF{y0u_m4d3_1t_d846125f7bdbf4d6e89cbc5edb6fa739}
?> 
```
Required flag: picoCTF{y0u_m4d3_1t_d846125f7bdbf4d6e89cbc5edb6fa739}


