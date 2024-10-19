# 🏠 Real Estate Price Prediction Website

![Project Screenshot](https://github.com/Ericazzzzzz/Real-Estate-Price-Prediction/blob/main/BHP_website.PNG)

This data science project series walks through the step-by-step process of building a real estate price prediction website. Below are the key components of the project, technologies used, and the steps to deploy it to the cloud.

---

## 🚀 Overview:
This project builds a machine learning model using `sklearn` and linear regression on the Bangalore home prices dataset from Kaggle. A Python Flask server handles HTTP requests, and the website, built with HTML, CSS, and JavaScript, allows users to enter house features (e.g., square footage, bedrooms) and get a predicted price.

---

## 🔑 Key Components:

1. **🛠️ Model Building**: 
   - Built using `sklearn` and linear regression with data from Bangalore home prices.
   - Key Concepts:
     - 📊 Data cleaning, outlier detection, and feature engineering.
     - 📉 Dimensionality reduction, GridSearchCV for hyperparameter tuning, and k-fold cross-validation.

2. **🌐 Python Flask Server**: 
   - Develop a Python Flask server to handle HTTP requests and serve the predicted price using the trained model.

3. **💻 Web Interface**: 
   - Build a user-friendly interface with **HTML**, **CSS**, and **JavaScript**. Users can input home details, and the interface fetches predictions from the Flask server.

---

## 🧰 Technologies & Tools:

- **Python**
- **Numpy and Pandas** for data cleaning.
- **Matplotlib** for data visualization.
- **Scikit-learn** for model building.
- **Jupyter Notebook**, **Visual Studio Code**, and **PyCharm** as IDEs.
- **Python Flask** for building the server.
- **HTML/CSS/JavaScript** for the user interface.
- **Nginx** for web server setup.
- **AWS EC2** for cloud deployment.

---

## ☁️ Deployment to Cloud (AWS EC2):

### 1. **Setup EC2 Instance**:
- Create an EC2 instance using AWS, configure the security group to allow HTTP traffic.

### 2. **Connect to EC2 via SSH**:
   ```bash
   ssh -i "path/to/your/key.pem" ubuntu@your-ec2-instance-url
   ```

### 3. **Nginx Setup**:
- Install and configure `nginx` to serve the website.
   ```bash
   sudo apt-get update
   sudo apt-get install nginx
   sudo service nginx start
   ```

### 4. **Deploy Code**:
- Use **WinSCP** or `git` to copy files to the EC2 instance.
- Setup `nginx` to point to your app.

Example Nginx configuration:
   ```nginx
   server {
       listen 80;
       server_name bhp;
       root /home/ubuntu/BangloreHomePrices/client;
       index app.html;
       location /api/ {
           proxy_pass http://127.0.0.1:5000;
       }
   }
   ```

### 5. **Create Symlink and Restart Nginx**:
   ```bash
   sudo ln -s /etc/nginx/sites-available/bhp.conf /etc/nginx/sites-enabled/
   sudo unlink /etc/nginx/sites-enabled/default
   sudo service nginx restart
   ```

### 6. **Install Python Packages and Start Flask Server**:
   ```bash
   sudo apt-get install python3-pip
   sudo pip3 install -r /home/ubuntu/BangloreHomePrices/server/requirements.txt
   python3 /home/ubuntu/BangloreHomePrices/client/server.py
   ```

### 7. **Access the Website**:
   - Visit your EC2 instance's public URL in the browser.

   Example: `http://your-ec2-instance-url/`

---

Enjoy a fully functional real estate price prediction website deployed in the cloud!


