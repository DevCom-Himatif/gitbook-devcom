---
description: 24 Februari 2020
---

# Developer Starter Pack

## Requirement 🛠 

1. [VSCode](https://aka.ms/win32-x64-user-stable) 
2. [Git](https://github.com/git-for-windows/git/releases/download/v2.25.0.windows.1/Git-2.25.0-64-bit.exe) 
3. Daftar [gitlab](https://gitlab.com/) menggunakan Google OAuth / E-mail

## Software Developer 👨💻 

Software Developer == Software Engineer

Choose your route:

* Desktop Software Developer \(C\#, Visual Basic\)
* Web Front-end Developer \(HTML, CSS, JS\) \(Client Side\)
* Web Back-end Developer \(JS, MySQL, NoSQL\) \(Server Side\)
* Web Full-stack Developer
* Android Native Developer \(Java, Kotlin\)
* iOS Native Developer \(Swift\)
* Hybrid Mobile Developer \(React Native, Flutter\)

## Weaponry 💻 

* Text Editor with snippets and plug-in 
* Small knowledge about navigating in CLI 
* Command Prompt/Terminal
* Google 
* Git

## CLI \(Command Line Interface\) ⌨ 

Command Prompt `Windows + R > cmd > Enter`

![CMD In windows](../.gitbook/assets/image%20%2830%29.png)

Cara lain membuka cmd, ketikan cmd di folder direktori yang diinginkan

![Cara lain membuka CMD](../.gitbook/assets/image%20%286%29.png)

## Command Prompt 🖥 

#### Show files in current directory

```text
$ dir 
```

```text
$ dir /b
```

#### 

#### Go to Specific directory \(use TAB for autocomplete\)

```text
$ cd FolderDevcom
```

```text
$ cd ..
```



#### Create Directory or Folder

```text
$ mkdir FolderDevcom
```



#### Open Program

```text
$ notepad
```



#### Create File

```text
$ notepad Profil.txt
```



#### Environment Variables

`This PC > Right Click > Properties > Advanced System Settings > Environment Variables > System Variables > Path`

![Letak Environment Variables](../.gitbook/assets/image%20%282%29.png)

#### 

#### Package Manager 

Package manager di windows ada [Chocolatey](https://chocolatey.org/)

**Windows** 

```text
$ choco install python
```

**Linux** 

```text
$ sudo apt-get install python
```

## Text Editor

* Notepad++

![Notepad++](../.gitbook/assets/image%20%2810%29.png)

* Sublime

![Sublime](../.gitbook/assets/image%20%2813%29.png)

* Atom

![Atom](../.gitbook/assets/image%20%2824%29.png)

* VSCode

![VSCode](../.gitbook/assets/image%20%2822%29.png)

* Vim

![Vim](../.gitbook/assets/image%20%2814%29.png)

#### 

#### Open VSCode via CLI

```text
$ code
```



#### Install Plugin Terminal in VSCode

![Plugin Terminal in VSCode](../.gitbook/assets/image%20%283%29.png)



#### Compile C++ Program in VSCode

1. Buat Folder bernama `FolderDevcom`
2. Buat File bernama `print.cpp`
3. Isi dengan kodingan dibawah 
4. ```text
   #include<iostream>

   using namespace std;

   int main(int argc, char* argv[]) { 
       for (int i = 0; i < argc; ++i) 
           cout << argv[i] << "\n"; 
  
       return 0; 
   }
   ```
5. Compile codingan menggunakan command:
6. ```text
   $ g++ -o print print.cpp
   ```
7. ```text
   $ print "Developer Community"
   ```

## git

* What is git ?
* What is git clone?
* What is git commit?
* What is git push?

#### Version Control System \(VCS\)

![Source: GoAcademy](../.gitbook/assets/image%20%2821%29.png)



![git illustration](../.gitbook/assets/image%20%2816%29.png)



### 2 ways to use git

* Push **Local Repository** to create new **Remote Repository**
* Create **Remote Repository** and clone it to **Local Repository**

#### **Git global setup**

```text
git config --global user.name "Arif R Gilang"
git config --global user.email "arifrgilang@gmail.com"
```

\*\*\*\*

**Local to Remote**

```text
cd FolderDevcom
git init
git remote add origin https://gitlab.com/arifrgilang/latihan-devcom.git
git add print.cpp
git add .
git commit -m "Menambahkan program print text"
git push -u origin master
```



#### **Remote to Local**

```text
git clone https://gitlab.com/arifrgilang/latihan-devcom.git
cd latihan-devcom
notepad print.cpp
git add print.cpp
git commit -m "Menambahkan program print text"
git push -u origin master
```



#### **Multiple person working on one project**

```text
// before pushing, ALWAYS DO THIS!

git status
git pull
```



### Advanced Git

![Development using git](../.gitbook/assets/image%20%284%29.png)



![Branches Hierarchy](../.gitbook/assets/image%20%2823%29.png)

#### More at [git documentation](https://git-scm.com/doc)

## Protip



