Criar ambiente virtual reservado para boas praticas. ("python -m venv <nomeDoVirtualEnv>" --> "cd <nomeDoVirtualEnv>" -> "cd Scripts" --> ".\activate")

Selecionar a pasta fora do raiz que contém o VirtualEnv.

1. instalar o Django com o comando "pip install Django".



2. configurar o banco de dados que irá trabalhar.



3. criar projeto usando Django com o comando "django-admin startproject <nomeDoProjeto> .". (Para não criar uma subpasta dentro do projeto digite espaço seguido de um ponto após o nome do projeto)
**Explicação dos arquivos criados:
   - O diretório mysite/ interior é o pacote Python para o seu projeto. Seu nome é o nome do pacote Python que você vai precisar usar para importar coisas do seu interior (por exemplo, mysite.urls).
   - manage.py: um utilitário de linha de comando que permite a você interagir com esse projeto Django de várias maneiras. Você pode ler todos os detalhes sobre o manage.py em django-admin and manage.py.
   - mysite/__init__.py: um arquivo vazio que diz ao Python que este diretório deve ser considerado um pacote Python. Se você é um iniciante Python, leia mais sobre pacotes na documentação oficial do Python.
   - mysite/asgi.py: um ponto de integração para servidores web compatíveis com ASGI usado para servir seu projeto. Veja Como fazer o deploy com ASGI para mais detalhes. 
   - mysite/settings.py: configurações para este projeto Django. Configurações do Django irá revelar para você tudo sobre o funcionamento do settings.
   - mysite/urls.py: as declarações de URLs para este projeto Django; um “índice” de seu site movido a Django. Você pode ler mais sobre URLs em Despachante de URL. 
   - mysite/wsgi.py: um ponto de integração para servidores web compatíveis com WSGI usado para servir seu projeto. Veja Como implementar com WSGI para mais detalhes. 



4.a. rodar o servidor django, ir no directory "my site" e executar o comando "py manage.py runserver".
**abrindo o servidor, digitar "/admin" para acessar as permissões do banco de dados.
**alterar porta de acesso "py manage.py runserver <numeroDaPorta>"
**alterar ip do computador "py manage.py runserver <numeroDoIP>" (o que é útil se estiver usando Vagrant ou quer mostrar seu trabalho para outros computadores na rede, 0 é um atalho para 0.0.0.0. A documentação completa para o servidor de desenvolvimento pode ser encontrada na referência do runserver ).

4.b. criar diretorios de forma simples com o comando "py manage.py startapp polls"

4.c. dentro do diretorio criado, editar a polls/views.py com o codigo :
"   from django.http import HttpResponse


    def index(request):
        return HttpResponse("Hello, world. You're at the polls index.")  "

4.d. alterar o URLconf, crie um arquivo chamado urls.py dentro do diretorio polls e inclua o codigo:
"   from django.urls import path

    from . import views

    urlpatterns = [
        path('', views.index, name='index'),
    ]   "
Para apontar a URL criada vá em "mysite/urls.py", adicione a importação "django.urls.include" e insira um include() na lista de urlpatterns com o apontamento para a url, exemplo:
"   from django.contrib import admin
    from django.urls import include, path

    urlpatterns = [
        path('polls/', include('polls.urls')),
        path('admin/', admin.site.urls),
    ]   "
(Deve-se sempre usar include() quando você incluir outros padrões de URL. admin.site.urls é a única exceção a isso.)



5. digite o comando "py manage.py migrate" para executar outros bancos de dados.



7. digite o comando "py manage.py createsuperuser" para criar um super usuario.



USANDO CRUD
8. digite o comando "py manage.py startapp core" para criar a pasta core(cria  oque se identifica como 'coração' da aplicação)



9. criando o core deve-se registrar ele no "app/settings.py" na lista de apps instalados.



10. criar pasta templates dentro da pasta core e indexar suas paginas html e pasta static para indexar css e imagem.



11. verificar os passos 4 para direcionar corretamente o URL para as pastas corretas.



12. em "core/models.py" criar uma classe que herda do models.Model.



13. em "core/admin" registre sua classe criada em models. 
 - Coloque a classe dentro do comando "admin.site.register(<nomeDaClasseCriada>". 
 - Execute no terminal o comando "python manage.py makemigrations" e verifique se criou dentro de migrations respectiva para clase, onde deverá descrever como os itens da classe deve ser criado. 
 - Execute no terminal "python manage.py migrate" para criar a tabela dentro do banco de dados.
*Se quiser registrar de maneira limpa adicione o __str__ metodo e retorne o valor colocado.



LER
14. em "core/views.py" crie um objeto que receba a classe criada em models e use o ".objects.all()" para retornar todos as informações dentro da classe criada.
* Use o Jinja no html para mostrar o resultado.


CRIAR
15. 
