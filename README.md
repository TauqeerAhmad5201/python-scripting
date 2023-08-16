# python-scripting
python-scripting

### Resource 

https://www.redhat.com/sysadmin/python-scripting-intro

### Python scripting is used in DevOps for a variety of reasons, including:

- It is a powerful and versatile language. Python can be used to automate a wide range of tasks, from simple to complex.
- It is easy to learn and use. Python has a simple syntax that is easy to understand, even for beginners.
- It is open source and free to use. This makes it a cost-effective choice for many organizations.

### Here are some examples of Python scripts that you can use to analyze data:

- A script that cleans and analyzes data from a survey.

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


### script to read metadata of a PDF

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
# Python script to combine PDFs
```
#!/usr/bin/python3

from PyPDF2 import PdfWriter

merger = PdfWriter()

for pdf in ["page1.pdf", "page2.pdf", "page3.pdf"]:
    merger.append(pdf)

merger.write("merged-pdf.pdf")
merger.close()
```
# Python script to extract metadata

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
# Do something with the json response to prove it works. 

print(usa_json)
```
### Compile data from a webpage
```
import requests

response = requests.get('https://www.bbc.com/news')

print(response.status_code)

from bs4 import BeautifulSoup                          

soup = BeautifulSoup(response.content, 'html.parser') 

print(soup)
```
### looking for a setup
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


## Reading PDF Annotations
```
from PyPDF2 import PdfReader

reader = PdfReader("commented.pdf")

for page in reader.pages:
    if "/Annots" in page:
        for annot in page["/Annots"]:
            obj = annot.get_object()
            annotation = {"subtype": obj["/Subtype"], "location": obj["/Rect"]}
            print(annotation)
```



## Extract Images

```
from PyPDF2 import PdfReader

reader = PdfReader("example.pdf")

page = reader.pages[0]
count = 0

for image_file_object in page.images:
    with open(str(count) + image_file_object.name, "wb") as fp:
        fp.write(image_file_object.data)
        count += 1

```


## Youtube video downloader 

```
#!/usr/bin/python3

from pytube import YouTube

link = input('Enter the URL of the video')
yt = YouTube(link)

print(yt.title)

download = yt.streams.get_highest_resolution().download()

print('Done!')
```
##  Pull live traffic data

```
#!/usr/bin/python3
pip or pip3 install requests

#Which one you use (pip or pip3) depends on the version of Python and the package manager pip you're using

import requests


url_api = 'https://api.midway.tomtom.com/ranking/liveHourly/USA_los-angeles'

usa_req = requests.get(url_api)

usa_json = usa_req.json()

### Compile data from a webpage

```
pip or pip3 install beautifulsoup4

import requests

response = requests.get('https://www.bbc.com/news')

print(response.status_code)

from bs4 import BeautifulSoup                          

soup = BeautifulSoup(response.content, 'html.parser') 

print(soup)

print(soup.find_all('h2'))
```

    cropped_img.show()

    im.filter(ImageFilter.BoxBlur(5)).show()
```

```

    cropped_img = im.crop((300, 150, 700, 1000))
    print(cropped_img.size)

```

### image modification

```
#!/usr/bin/python3

from PIL import Image, ImageFilter

with Image.open("nature.jpg") as im:
    #show the original image
    # im.show("Original Image")
 
    #convert into grayscale
    # grayscaleImg = im.convert("L")
 
    # #show the grayscale image
    # grayscaleImg.show()

    # rotated_img = im.rotate(45)

    # rotated_img.show()

    print(im.format)
    print(im.size)

```

### Script to filter in excel 
```
import openpyxl

def filter_excel_sheet(excel_file, sheet_name, column_name, keyword):
  """Filters an Excel sheet by a keyword in a particular column.

  Args:
    excel_file: The path to the Excel file.
    sheet_name: The name of the sheet to filter.
    column_name: The name of the column to filter by.
    keyword: The keyword to filter for.

  Returns:
    The filtered Excel sheet.
  """

  workbook = openpyxl.load_workbook(excel_file)
  sheet = workbook[sheet_name]

  # Create a filter object for the column.
  filter_obj = sheet[column_name].autofilter

  # Set the filter criteria to the keyword.
  filter_obj.criteria1 = keyword

  # Apply the filter.
  filter_obj.apply()

  # Return the filtered sheet.
  return workbook[sheet_name]


if __name__ == "__main__":
  excel_file = "my_data.xlsx"
  sheet_name = "Sheet1"
  column_name = "Skills"
  keyword = "Basic-moderate"

  filtered_sheet = filter_excel_sheet(excel_file, sheet_name, column_name, keyword)

  print(filtered_sheet)
```

### Python script to generate Password
