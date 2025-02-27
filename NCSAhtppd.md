### **Hosting a Static `index.html` Page in NCSA HTTPd**  

NCSA HTTPd was one of the first web servers, developed at the National Center for Supercomputing Applications (NCSA). If you're working with it on an old UNIX-based system, follow these steps to host a static HTML page.

---

### **1. Install NCSA HTTPd**  
If you don't have it installed, download an old version from an archive (since it's no longer maintained).

```sh
wget http://archive.ncsa.uiuc.edu/SDG/Software/Mosaic/Unix/ncsa_httpd-1.5.tar.gz
tar -xvzf ncsa_httpd-1.5.tar.gz
cd ncsa_httpd-1.5
```

Compile it:
```sh
make
```

After successful compilation, the `httpd` binary will be available.

---

### **2. Configure NCSA HTTPd**  
Create the configuration file, typically located at `/usr/local/etc/httpd.conf` or `/etc/httpd.conf`.

Edit or create the file:
```sh
nano /usr/local/etc/httpd.conf
```

Add the following configuration:
```ini
ServerRoot /usr/local/etc/httpd
DocumentRoot /var/www/html
Port 8080
User nobody
Group nobody
DirectoryIndex index.html
```

---

### **3. Create the Document Root and an HTML File**  
Create the directory where your web pages will be stored:

```sh
mkdir -p /var/www/html
```

Create a simple `index.html` page:

```sh
nano /var/www/html/index.html
```

Add the following content:
```html
<!DOCTYPE html>
<html>
<head>
    <title>NCSA HTTPd Server</title>
</head>
<body>
    <h1>Welcome to NCSA HTTPd Server</h1>
</body>
</html>
```

Save and exit (`CTRL + X`, then `Y`, then `ENTER`).

---

### **4. Start the NCSA HTTPd Server**  

Run the server with the following command:

```sh
/usr/local/etc/httpd -f /usr/local/etc/httpd.conf
```

If you want to run it in the background:

```sh
/usr/local/etc/httpd -f /usr/local/etc/httpd.conf &
```

---

### **5. Access the Web Server**  
Now, open your browser and visit:

```
http://localhost:8080
```

You should see your `index.html` page.

---

### **6. Stop the NCSA HTTPd Server**  
To stop the server, find its process ID (PID) and kill it:

```sh
ps aux | grep httpd
kill -9 <PID>
```

---

### **Alternative: Using Python’s Simple HTTP Server**  
If you can't use NCSA HTTPd but need a simple static server:

```sh
cd /var/www/html
python3 -m http.server 8080
```

Would you like to troubleshoot any issues or configure logging? 🚀
