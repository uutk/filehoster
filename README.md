# filehoster
A over-complicated and buggy filehoster that uses mongodb

# Badges
[![Run on Repl.it](https://repl.it/badge/github/SnapDragon7410/filehoster)](https://repl.it/github/SnapDragon7410/filehoster)![Lint](https://github.com/SnapDragon7410/filehoster/workflows/Lint/badge.svg)

# How to start
## Step 1
Set the following Environmental Vars:
  
  `db` - Your MongoDB URL
  
  `adminuser` - Your admin username, will be explained later
  
  `adminpass` - Your admin username, will be explained later

## Step 2
Install requirements using the following command in terminal:
``` bash
python3 -m pip install -r requirements.txt --user
```

## Step 3
Start the service:
``` bash
python3 -m filehoster
```

# How to run on repl.it
Press the `run on repl` badge at the top of the README.md
Then in repl.it create a .env with the following details:
```
db = MongoDB-link
adminuser = YourAdminUsername
adminpass = YourAdminPassword
```
None of these should be in `""`

# How to use
## yourlink.com/upload
## methods=["GET", "POST"]
This is where you will be able to upload files through the UI

## yourlink.com/download
## methods=["GET"]
Here you will directed to a page where you can input your filename you have upload and be redirected to the download link
### yourlink.com/download/&ltfilename&gt
### methods=["GET"]
Simply replace &ltfilename&gt with a filename of that has been uploaded

## yourlink.com/api
## methods=["POST"]
This is a simple api that can receive a file that has been sent. This must be sent in the request argument "files" and the in the format of `file=file` or `{"file": file}`.

Then you will receive a json in the format of:
``` python
{'success': True or False, 'error': ErrorType}
```

## yourlink.com/delete?user=user&pass=pass&filename=filename
## methods=["DELETE"]
This is where `adminuser` and `adminpass` will be explained!

If the user and pass is not the same as the adminusername and adminpassword it will throw a 405 Forbidden HTTP Error.

This gives you the right to delete files that has been stored on your database.