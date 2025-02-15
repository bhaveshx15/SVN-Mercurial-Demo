# Version Control Experiment with Subversion (SVN) and Mercurial (Hg)

## **1. Subversion (SVN) Experiment**

### **Step 1: Create an SVN Repository**
```bash
mkdir -p ~/Desktop/DevOps/myrepo
svnadmin create ~/Desktop/DevOps/myrepo
```
![Screenshot](https://github.com/bhaveshx15/SVN-Mercurial-Demo/blob/main/images/Screenshot%20from%202025-02-15%2021-41-05.png)


### **Step 2: Checkout the Repository**
```bash
cd ~/Desktop/DevOps
svn checkout file:///$(pwd)/myrepo myproject
```
**Output:**
```
Checked out revision 0.
```

### **Step 3: Add and Commit a File**
```bash
cd myproject
echo "Hello SVN" > file.txt
svn add file.txt
svn commit -m "Added file.txt"
```

### **Step 4: Check the Log and Update**
```bash
svn log
svn update
```
![Screenshot from 2025-02-15 21-52-59](https://github.com/user-attachments/assets/a2ce8738-228d-419c-8fac-730c9671b599)


## **2. Mercurial (Hg) Experiment**

### **Step 1: Initialize a Mercurial Repository**

![Screenshot from 2025-02-15 21-57-22](https://github.com/user-attachments/assets/2b6e127e-9de8-4901-8a22-10f8d01fadad)

```bash
mkdir -p ~/Desktop/DevOps/brepo
cd ~/Desktop/DevOps/brepo
hg init
```
![Screenshot from 2025-02-15 22-29-53](https://github.com/user-attachments/assets/3a675e63-1e6f-4dd7-a16a-a7301bb046d6)


### **Step 2: Configure Username**
```bash
hg config --edit
```
Modify `[ui]` section to:
```ini
[ui]
username = asus <asus@example.com>
```

### **Step 3: Add and Commit a File**
```bash
echo "Hello Mercurial" > file.txt
hg add file.txt
hg commit -m "Added file.txt"
```
![Screenshot from 2025-02-15 22-29-53](https://github.com/user-attachments/assets/a1dcb3a4-3f8b-4267-970b-97a8be3e4a89)


### **Step 4: Clone the Repository**
```bash
cd ~/Desktop/DevOps
hg clone brepo myclone
```
![Screenshot from 2025-02-15 22-30-17](https://github.com/user-attachments/assets/31bb2017-af4b-43e9-b9e3-414d2ac3688e)


### **Step 5: Make Changes and Pull Updates**
```bash
cd brepo
echo "Another line" >> file.txt
hg commit -m "Updated file.txt with another line"
```

Now, pull updates in `myclone`:
```bash
cd ~/Desktop/DevOps/myclone
hg pull
hg update
```
![Screenshot from 2025-02-15 22-30-49](https://github.com/user-attachments/assets/2d12a5e1-e295-448d-a421-0e613dbaa61d)


## **3. Hosting index.html with Readme.md on GitHub Pages**
1. **Create an `index.html` file** in your repository:
```
`<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SVN & Mercurial Report</title>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
            background-color: #f4f4f4;
        }
        #content {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body>
    <h2>SVN & Mercurial Practical Report</h2>
    <div id="content">Loading...</div>

    <script>
        fetch('README.md')
            .then(response => response.text())
            .then(text => {
                document.getElementById('content').innerHTML = marked.parse(text);
            })
            .catch(error => {
                document.getElementById('content').innerHTML = "<p>Error loading README.md</p>";
            });
    </script>
</body>
</html>
```

2. **Push Files to GitHub:**
```bash
git init
git add experiment.md index.html
git commit -m "Added experiment report and index.html"
git branch -M main
git remote add origin https://github.com/your-username/version-control-experiment.git
git push -u origin main
```

3. **Enable GitHub Pages:**
   - Go to **Repository Settings > Pages**.
   - Select **Branch: main** and save.

**Hosted Website Link**
https://bhaveshx15.github.io/SVN-Mercurial-Demo/



