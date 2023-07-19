# python-scripting
python-scripting

### Resource 

https://www.redhat.com/sysadmin/python-scripting-intro

# Python script to test speed 

```
# Internet Speed tester
# pip install speedtest-cli

#!/usr/bin/python3
import speedtest as st

# Set Best Server
server = st.Speedtest()
server.get_best_server()

# Test Download Speed
down = server.download()
down = down / 1000000
print(f"Download Speed: {down} Mb/s")

# Test Upload Speed
up = server.upload()
up = up / 1000000
print(f"Upload Speed: {up} Mb/s")

# Test Ping
ping = server.results.ping
print(f"Ping Speed: {ping}")

````

### Changing the executable permission of the script file

chmod +x {script_name}.py

` could have written as u+x -> denoting the changes for you/yourself`

### Running a script 

./{script_name}.py


# Python script to send email
```
import smtplib
 
# creates SMTP session
s = smtplib.SMTP('smtp.gmail.com', 587)
 
# start TLS for security
s.starttls()
 
# Authentication
s.login("sender_email_id", "sender_email_id_password")
 
# message to be sent
message = "Message_you_need_to_send"
 
# sending the mail
s.sendmail("sender_email_id", "receiver_email_id", message)
 
# terminating the session
s.quit()
```

### 

1. Requests

Python Requests allows you to send HTTP requests. Using this module, we can post or retrieve the data from a Rest API. There are many methods included in this module, like:

    GET
    POST
    PUT
    DELETE

All these methods perform particular actions like adding a comment (PUT), retrieving data (GET), or deleting a user field (DELETE).




```
#!/usr/bin/python3

from PyPDF2 import PdfReader

reader = PdfReader("statement.pdf")

meta = reader.metadata

print(len(reader.pages))

# All of the following could be None!
print(meta.author)
print(meta.creator)
print(meta.producer)
print(meta.subject)
print(meta.title)
```
