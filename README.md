# Soupbowl Website

![image][h]

[![License CC BY-SA](https://img.shields.io/github/license/soup-bowl/soupbowl.io)](http://creativecommons.org/licenses/by-sa/4.0/)
![Website](https://img.shields.io/website?down_message=offline&up_message=online&url=https%3A%2F%2Fsoupbowl.io)
[![CodeFactor](https://www.codefactor.io/repository/github/soup-bowl/soupbowl.io/badge)](https://www.codefactor.io/repository/github/soup-bowl/soupbowl.io)

The main **[soupbowl.io][s]** website, but in automatic build-and-deploy [Jekyll][j] flavour.

**This is a personal blog - Pull Requests will not be accepted.** This site is currently hosted using **[GitHub Pages][gh]**.

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/soup-bowl/soupbowl.io)

## 🧪 Compiling with Jekyll

Installation of Ruby, Gem, Jekyll, etc is **not necessary**, as the **Docker Compose** script included with the repository will run the process for you. Upon running `docker-compose up`, the `_site` directory will be created and re-populated upon each edit.

## NGINX Configuration

**This is legacy and does not reflect the latest setup.**

The current configuration for this site is as follows:

```
server {
	listen 80;
	listen [::]:80;
	server_name beta.soupbowl.io;
	return 301 https://$server_name$request_uri;
}

server {
	include snippets.d/soupbowl-cert.conf;
	add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
	server_name beta.soupbowl.io;
	root /www/beta.soupbowl.io;
	index index.html;
	error_page 404 /404.html;

	location / {
		try_files $uri $uri.html $uri/ $uri/index.html =404;
	}

	location = /404.html {
		internal;
	}
}
```

* First `server` block is to enforce HTTPS.
* First `location` block is to catch URLs that do not end in '.html' and try them as if they did.

[h]:  https://user-images.githubusercontent.com/11209477/147856239-c7eb65c9-ba89-44fa-bf32-1e68568dc48b.png
[s]:  https://www.soupbowl.io
[gh]: https://docs.github.com/en/pages
[j]:  https://jekyllrb.com/
