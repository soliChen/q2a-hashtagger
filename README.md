# q2a-hashtagger

When I want to add the mention user (@username) function to My Q2A ,finally I found out this q2a plugin:

https://github.com/ProThoughts/q2a-hashtagger

I found it work with no-sapce username like "@abc" or "@a-b-c" but not "@a b c".


I read the code , I found that in "qa-hashtagger.php" , line 378 and 383 , we see the match rule as follow:

    $row['content'] = $this->preg_call('%@(?P<name>[\w\-]+)%u', 'build_user_link', $row['content']);

We would like to add the space ("\ ") like this:

    $row['content'] = $this->preg_call('%@(?P<name>[\w\-\ ]+)%u', 'build_user_link', $row['content']);

It works, one thing:

If you add "@user" in front of your content, you will lose the style of content.

You should add this function at the end of your content.

Other bugs? I don't know yet :)

Soli
