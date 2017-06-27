# q2a-hashtagger

When I want to add the mention user (@username) function to My Q2A ,finally I found out this q2a plugin:

https://github.com/ProThoughts/q2a-hashtagger

<br>
I found it work with no-sapce username like "@abc" or "@a-b-c" but not "@a b c".

I read the code , I found that in "qa-hashtagger.php" , line 378 and 383 , we see the match rule as follow:

    $row['content'] = $this->preg_call('%@(?P<name>[\w\-]+)%u', 'build_user_link', $row['content']);

We would like to add the space ("\ ") like this:

    $row['content'] = $this->preg_call('%@(?P<name>[\w\-\ ]+)%u', 'build_user_link', $row['content']);

<br>
It works, one thing:
<br><br>
I still find out that the style of content will lose and become one line, like :
<br><font color='red'>
abc<br>
def<br>
@ admis
<br><br>
become to :
<br><br><font color='red'>
abc def @ admis</font>
<br><br>
So sad.
<br><br>
But, after testing , I found out that if we use the "Insert a quote" (on Q2A's editor,in Chinese is "引用段落") and write "@ admis" inside , style keeps fine.

Other bugs? I don't know yet :)
<br><br>
Soli
