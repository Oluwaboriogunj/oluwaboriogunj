pip install pandas openpyxl schedule
import pandas as pandas
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
import schedule
import time
from datetime import datetime, timedelta

# Function to send email
def send_email(to_email, subject, body):
    from_email = 'hubersocial171@gmail.com'  
    password = 'intern2024'  

    msg = MIMEMultipart()
    msg['From'] = from_email
    msg['To'] = to_email
    msg['Subject'] = subject

    msg.attach(MIMEText(body, 'plain'))

    with smtplib.SMTP('smtp.gmail.com', 587) as server:
        server.starttls()
        server.login(from_email, password)
        server.sendmail(from_email, to_email, msg.as_string())
