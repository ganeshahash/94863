app.py# 94863import os
from zipfile import ZipFile

app_py = '''# (insira aqui o código Python do app.py que te mandei acima — com HTML_TEMPLATE, login e análise)'''

requirements_txt = "Flask\nFlask-Cors\nccxt\npandas\npandas-ta\ngunicorn\n"
procfile = "web: gunicorn app:app"

os.makedirs("flask_cripto_app", exist_ok=True)

with open("flask_cripto_app/app.py", "w") as f:
    f.write(app_py)
with open("flask_cripto_app/requirements.txt", "w") as f:
    f.write(requirements_txt)
with open("flask_cripto_app/Procfile", "w") as f:
    f.write(procfile)

with ZipFile("flask_cripto_app.zip", "w") as zipf:
    for root, _, files in os.walk("flask_cripto_app"):
        for file in files:
            zipf.write(os.path.join(root, file), os.path.relpath(os.path.join(root, file), "flask_cripto_app"))

print("ZIP gerado com sucesso: flask_cripto_app.zip")
