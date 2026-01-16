## Part 1
```bash
ssh-keygen -t ed25519 -f ~/.ssh/wkone
```
`-t` is specifying the encryption algorithm

`-f` is specifying the location of key file is stored 

## Part 3

```bash
export username="admin"
export ip_address="<Your EC2 IP Address>"
export ssh_key_path="~/.ssh/wkone"
```

```bash
#!/bin/bash
ssh -i $ssh_key_path $username@$ip_address << EOF
sudo apt update -y
sudo apt install nginx -y
sudo systemctl enable --now nginx
EOF
```


```bash
#!/bin/bash
ssh -i $ssh_key_path $username@$ip_address << EOF
	cat <<- DELIMITER > ~/index.html
	<!DOCTYPE html>  
	<html lang='en'>  
	<head>  
	  <meta charset='UTF-8'>  
	  <meta name='viewport' content='width=device-width, initial-scale=1.0'>  
	  <title>Hello World</title>  
	</head>  
	<body>  
	  <h1>Hello World!</h1>  
	  <p>Today's date is: $(date "+%d/%m/%Y")</p>  
	</body>  
	</html>
	DELIMITER
	sudo mv ~/index.html /var/www/html/index.nginx-debian.html
EOF
```

## DEMO

### IP Address of instance
![](https://github.com/tony-nlc/acit4640-Lab2/blob/main/Pasted%20image%2020260116151507.png)

### Index Homepage
![](https://github.com/tony-nlc/acit4640-Lab2/blob/main/Pasted%20image%2020260116151435.png)
