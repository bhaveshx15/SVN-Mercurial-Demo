# Version Control Experiment with Subversion (SVN) and Mercurial (Hg)

## **1. Subversion (SVN) Experiment**

### **Step 1: Create an SVN Repository**
```bash
mkdir -p ~/Desktop/DevOps/myrepo
svnadmin create ~/Desktop/DevOps/myrepo
```

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

## **2. Mercurial (Hg) Experiment**

### **Step 1: Initialize a Mercurial Repository**
```bash
mkdir -p ~/Desktop/DevOps/brepo
cd ~/Desktop/DevOps/brepo
hg init
```

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

### **Step 4: Clone the Repository**
```bash
cd ~/Desktop/DevOps
hg clone brepo myclone
```

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

## **3. Hosting index.html with experiment.md on GitHub Pages**
1. **Create an `index.html` file** in your repository:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Version Control Experiment</title>
</head>
<body>
    <h1>Version Control Experiment</h1>
    <p><a href="experiment.md">View experiment.md</a></p>
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



