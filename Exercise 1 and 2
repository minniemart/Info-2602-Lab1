from flask import Flask, request, jsonify
import json

app = Flask(__name__)

# Load data from JSON file
with open('data.json') as f:
    data = json.load(f)

@app.route('/')
def hello_world():
    return 'Hello, World!' 

@app.route('/students')
def get_students():
    return jsonify(data)


@app.route('/students/<id>')
def get_student(id):  
    for student in data: 
        if student['id'] == id:
            return jsonify(student)
 
    return jsonify({"error": "Student not found"}), 404


##Exercise1

@app.route('/stats')
def get_stats():
  
    meal_preferences = {

        "Chicken": 0,
        "Fish": 0,
        "Vegetable": 0,
    }

    for student in data:
        
         pref = student.get('pref', 'Not Specified')
         if pref in meal_preferences:
            meal_preferences[pref] += 1
      

   
    programmes = {
        "Computer Science (Major)": 0,
        "Computer Science (Special)": 0,
        "Information Technology (Major)": 0,
        "Information Technology (Special)": 0
    }

    
    for student in data:
        prog = student.get('programme', 'Not Specified')
        if prog in programmes:
            programmes[prog] += 1

    
    
    stats = {
        "meal_preferences": meal_preferences,
        "programmes": programmes
    }

    
    return jsonify(stats)

##Exercise 2

@app.route('/add/<a>/<b>')
def add(a, b):
   
   
    num1 = int(a)
    num2 = int(b)
    result = num1 + num2

    return jsonify({
      
        "a": num1,
        "b": num2,
        "result": result
    })

@app.route('/subtract/<a>/<b>')
def subtract(a, b):
    
    num1 = int(a)
    num2 = int(b)
    result = num1 - num2

    return jsonify({
        
        "a": num1,
        "b": num2,
        "result": result
    })

@app.route('/multiply/<a>/<b>')
def multiply(a, b):
   
    num1 = int(a)
    num2 = int(b)
    result = num1 * num2

    return jsonify({
       
        "a": num1,
        "b": num2,
        "result": result
    })

@app.route('/divide/<a>/<b>')
def divide(a, b):
    

    num1 = float(a)
    num2 = float(b)


    if num2 == 0:
        return jsonify({
            "error": "Cannot divide by zero"
        }), 400

    result = num1 / num2

    return jsonify({
       
        "a": num1,
        "b": num2,
        "result": result
    })

if __name__ == '__main__':
    
    app.run(host='0.0.0.0', port=8080, debug=True)
