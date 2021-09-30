from flask import Flask, render_template

app = Flask(__name__)

@app.route('/static/<content>')
def static_content(content):
    return render_template(content)

@app.route('/name/<name>', methods=['GET'])
def ejemplo(name):
    return f"Hola, {name}"

@app.route('/palindromo', methods=['GET'])
def ejercicio1():
    texto = input("Ingrese una palabra: ").lower()
    rever = texto[::-1]

    if texto == rever:
      print("La palabra ingresada si es palindromo!!")
    else:
      print("La palabra ingresada no es palindromo!!")
    return

@app.route('/operaciones', methods=['GET'])
def ejercicio2():
    a,b = input()
    print('suma', a+b ,',resta', a-b,',multiplicacion', a*b,'division', a/b)
    return

@app.route('/ordenar', methods=['GET'])
def ejercicio3():
    a,b,c = input()
    numeros = a,b,c
    ordenados = sorted(numeros)
    print(ordenados)
    return


if __name__ == '__main__':
    app.secret_key = ".."
    app.run(port=8080, threaded=True, host=('127.0.0.1'))
