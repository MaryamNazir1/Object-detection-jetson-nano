# Install Python 3.8 on Jetson Nano

Follow these steps to install **Python 3.8** from source and set up a dedicated virtual environment.

---

## 1. Update System Packages

```bash
sudo apt update
sudo apt upgrade
```

---

## 2. Install Build Dependencies

```bash
sudo apt install build-essential libssl-dev zlib1g-dev \
libncurses5-dev libncursesw5-dev libreadline-dev libsqlite3-dev \
libgdbm-dev libdb5.3-dev libbz2-dev libexpat1-dev liblzma-dev \
libffi-dev libc6-dev
```

---

## 3. Download Python 3.8 Source Code

```bash
wget https://www.python.org/ftp/python/3.8.12/Python-3.8.12.tar.xz
```

---

## 4. Extract Archive

```bash
tar -xf Python-3.8.12.tar.xz
cd Python-3.8.12
```

---

## 5. Configure Build

```bash
./configure --enable-optimizations
```

---

## 6. Build Python

```bash
make -j4
```

---

## 7. Install Python 3.8

```bash
sudo make altinstall
python3.8 --version
```

Python 3.8 is now installed.

---

## 8. Create a Virtual Environment with Python 3.8

Exit the `Python-3.8.12` folder first:

```bash
cd ..
```

Then create and activate a virtual environment:

```bash
python3.8 -m venv myenv
source myenv/bin/activate
```

---

You now have **Python 3.8 installed** and a **separate virtual environment** ready for use on your Jetson Nano.

Install Jupyter Notebook

```bash
pip install jupyter notebook
```

then Start Jupyter Notebook

```bash
jupyter notebook
```
