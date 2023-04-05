Para exemplificar a implementação de um CRUD, vamos criar um recurso para gerenciamento de alunos, utilizando a linguagem de programação Python e o framework Flask. Nesse caso, nosso CRUD irá fornecer as seguintes operações:

Listar todos os alunos cadastrados;
Consultar os dados de um aluno específico;
Adicionar um novo aluno;
Atualizar os dados de um aluno existente;
Excluir um aluno.
Para isso, vamos criar uma aplicação Flask e definir as seguintes rotas:

GET /alunos: lista todos os alunos cadastrados;
GET /alunos/:id: retorna os dados de um aluno específico;
POST /alunos: adiciona um novo aluno;
PUT /alunos/:id: atualiza os dados de um aluno existente;
DELETE /alunos/:id: exclui um aluno.
Para executar essa aplicação, precisaremos instalar o Flask. Para isso, basta executar o seguinte comando no terminal:

pip install Flask

Com o Flask instalado, podemos criar nossa aplicação:

from flask import Flask, jsonify, request

app = Flask(__name__)

# Dados iniciais
alunos = [
    {"id": 1, "nome": "João", "idade": 20},
    {"id": 2, "nome": "Maria", "idade": 22},
    {"id": 3, "nome": "Pedro", "idade": 21},
]

# Listar todos os alunos
@app.route("/alunos", methods=["GET"])
def listar_alunos():
    return jsonify(alunos)

# Consultar dados de um aluno específico
@app.route("/alunos/<int:id>", methods=["GET"])
def consultar_aluno(id):
    aluno = [aluno for aluno in alunos if aluno["id"] == id]
    if len(aluno) == 0:
        return jsonify({"erro": "Aluno não encontrado"}), 404
    return jsonify(aluno[0])

# Adicionar um novo aluno
@app.route("/alunos", methods=["POST"])
def adicionar_aluno():
    aluno = {"id": request.json["id"], "nome": request.json["nome"], "idade": request.json["idade"]}
    alunos.append(aluno)
    return jsonify(aluno), 201

# Atualizar os dados de um aluno existente
@app.route("/alunos/<int:id>", methods=["PUT"])
def atualizar_aluno(id):
    aluno = [aluno for aluno in alunos if aluno["id"] == id]
    if len(aluno) == 0:
        return jsonify({"erro": "Aluno não encontrado"}), 404
    aluno[0]["nome"] = request.json.get("nome", aluno[0]["nome"])
    aluno[0]["idade"] = request.json.get("idade", aluno[0]["idade"])
    return jsonify(aluno[0])

# Excluir um aluno
@app.route("/alunos/<int:id>", methods=["DELETE"])
def excluir_aluno(id):
    aluno = [aluno for aluno in alunos if aluno["id"] == id]
    if len(aluno) == 0:
        return jsonify({"erro": "Aluno não encontrado"}), 404
    alunos.remove(aluno[0])
    return jsonify({"mensagem": "Aluno excluído com sucesso"})

if __name__ == '__main__':
    app.run(debug=True)

