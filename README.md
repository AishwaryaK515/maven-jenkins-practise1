**Project 1:
Freestyle Build with Git & Maven** — the most fundamental Jenkins practice to understand Continuous Integration.

---

# ✅ **Project 1: Freestyle Build with Git & Maven**

### 🎯 **Goal:**

Clone a Java Maven project from GitHub and build it inside Jenkins using Maven. 

---

## 🧰 Tools Used:

* **Jenkins**
* **Git*
* **Maven**
* **Java (JDK)**

---

## 🗂️ Project Folder (Example Layout):

```
jenkins-maven-sample/
├── src/
│   └── main/java/com/demo/App.java
├── pom.xml
```

Your project should have a valid `pom.xml` with `<packaging>jar</packaging>` or `<packaging>war</packaging>`, and a basic Java file.

---

## 🔧 Step-by-Step Guide

---

### 🔹 **Step 1: Install Required Tools in Jenkins**

Go to: **Manage Jenkins → Global Tool Configuration**

1. **Maven**

   * Name: `Maven3`
   * Check “Install automatically”
2. **Git** (usually auto-installed)
3. **JDK** (optional, depends on Jenkins version)

---

### 🔹 **Step 2: Create Java Maven Project (Optional for Testing)**

If you don’t have a repo yet, create one with this:

```bash
mkdir jenkins-maven-sample && cd jenkins-maven-sample

mkdir -p src/main/java/com/demo
nano src/main/java/com/demo/App.java
```

Paste:

```java
package com.demo;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello Jenkins + Maven");
    }
}
```

Then, create `pom.xml`:

```bash
nano pom.xml
```

Paste:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.demo</groupId>
  <artifactId>jenkins-pipeline-demo</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>
</project>
```

Push this project to GitHub.

---

### 🔹 **Step 3: Create Jenkins Job (Freestyle)**

1. Go to Jenkins Dashboard
2. Click **New Item**
3. Name: `Freestyle-Maven-Build`
4. Type: **Freestyle Project**
5. Click **OK**

---

### 🔹 **Step 4: Configure Jenkins Job**

#### 📁 **Source Code Management**

* Select **Git**
* Enter your GitHub repo URL
* Add Git credentials if needed

#### ⚙️ **Build Section**

* Click **Add Build Step → Invoke top-level Maven targets**
* Set Goals:

```bash
clean package
```

* Select Maven version: `Maven3`

---

### 🔹 **Step 5: Run the Build**

Click **Save → Build Now**

Check Console Output:

```bash
[INFO] BUILD SUCCESS
```

Artifacts will be saved under:

```
target/jenkins-pipeline-demo-1.0-SNAPSHOT.jar
```

---

### 🔍 **Verify the Output**

On the Jenkins UI:

* Go to the build number → `target/` folder
* Click on `workspace` → check generated `.jar`

---

exactly how to verify the generated `.jar` or `.war` file in Jenkins** after your build completes.

---

### 🔍 **How to View the Generated Artifact (e.g., `.war` or `.jar`) in Jenkins Workspace**

1. Go to your Jenkins **Dashboard**
   📍 `http://<jenkins-server>:8080/`

2. Click on your job name
   👉 Example: `WAR-Build-and-Deploy`

3. Click on the **build number**
   👉 e.g., `#1`, `#2`, etc.

4. In the left sidebar, click **"Workspace"**

   ![Workspace link in Jenkins](https://www.jenkins.io/images/doc/book/pipeline/jenkins-workspace.png)
   *(If you don’t see it, enable “Keep this build’s workspace” in job config → Advanced)*

5. In the workspace view:

   * Click into the **`target/`** folder
   * You should see your generated artifact, e.g.:

     ```
     jenkins-sample.war
     ```




## 📌 What You Learned:

* How to create a Freestyle job
* How to link a Git repo
* How to use Maven inside Jenkins
* Where build artifacts are stored


