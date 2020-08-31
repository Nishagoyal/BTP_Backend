from flask import Flask, render_template, redirect, url_for, request,session
import pyodbc 
import pandas as pd
from werkzeug.security import generate_password_hash, check_password_hash
 
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello"

@app.route("/SignIn", methods=['GET', 'POST'])
def SignIn():
    try:
        error = None
        request_data=request.json
        print(request.json)
        #print(type(request.json))
        if request.method == 'POST':
            server = 'flask.database.windows.net' 
            database = 'flask12' 
            username = 'flask' 
            password = //write password
            cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
            cursor = cnxn.cursor()
            password=generate_password_hash("{request_data['password']}")

            #cursor.execute(f"INSERT INTO registration VALUES ('{request_data['org_name']}','{request_data['email_id']}','{request_data['password']}','{request_data['address']}','{request_data['category']}','{request_data['city']}','{request_data['state']}','{request_data['pincode']}')")
            cursor.execute(f"INSERT INTO registration VALUES ('{request_data['org_name']}','{request_data['email_id']}','{password}','{request_data['address']}','{request_data['category']}','{request_data['city']}','{request_data['state']}','{request_data['pincode']}')")
            cursor.execute("select * from registration")
            cnxn.commit()
            # rows = cursor.fetchall()
            # for row in rows:
            #     print(row, end='\n')

            sql_query = pd.read_sql_query('SELECT * FROM registration',cnxn)
            print(sql_query)
            print(type(sql_query))
            return "done"
    finally:
        
        cursor.close()
        cnxn.close()
       
   

        
if __name__ == "__main__":
    
   app.run(host='0.0.0.0', port=5000)
    
