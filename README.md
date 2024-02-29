# GitActions

GitHub Actions nos ofrece una amplia lista de 'triggers' que pueden lanzar nuestros 'workflows'. Algunos de los más comunes incluyen 'push', 'pull request', 'issue', 'issue comment', 'workflow dispatch', y 'schedule'.

## ¿Cómo funciona el 'trigger' de 'push'?
Cuando haces 'push' de un nuevo 'commit' en alguna rama que tú definas, puedes activar un 'workflow'.

Esta acción también se puede configurar para todas las ramas y puede especificar a qué ramas afectará mediante la opción 'branches'. Y con la opción 'paths' puedes especificar qué archivos deben modificarse para que el 'workflow' se active.


    on: #Acaparará los triggers de este workflow
	push: #El tipo de trigger: push
		branches: #Las ramas en las que se activará el workflow
			- 'main' #Se activará si se hace push en la rama main
			- 'releases/**' #O en la rama releases y derivados
		paths: #Serán las rutas que se tendrán en cuenta para activar el workflow
			- '**.js' #Todos los archivos .js en el repositorio

## ¿Cómo se utiliza el 'trigger' de 'pull request'?
El 'trigger' 'pull request' ofrece características muy similares al de 'push'. Esto incluye 'branches' y 'paths', y también incluye 'types', que te permite especificar sobre qué acciones sobre 'pull request' quieres que se active.

on: #Acaparará los triggers de este workflow
	pull_request: #El tipo de trigger: pr
		types: #Los estados que activarán el trigger
			- [opened, labeled] #Tomará los estados del PR
		branches: #Las ramas en las que se activará el workflow
			- 'releases/**' #En la rama releases y derivados
		paths: #Serán las rutas que se tendrán en cuenta para activar el workflow
			- '**.js' #Todos los archivos .js en el repositorio

## ¿Cómo manejar la opción 'issues' y 'issue comment'?
El 'trigger' 'issues' funciona de manera similar al 'pull request', y tiene los mismos 'types'. Sin embargo, 'issue comment' funciona cuando se hacen comentarios nuevos sobre un 'issue' o 'pull request', y también puedes especificar si la acción se ejecuta solo en los comentarios de un 'pull request'.

    on: #Acaparará los triggers de este workflow
	issues: #El tipo de trigger: issues
		types: #Los estados que activarán el trigger
			- [opened, edited, closed]
______________________________________________________________________________
    on:
	issue_comment: 
		types:  [created, deleted]
______________________________________________________________________________
    on: issue_comment
jobs:
	pr_commented:
		name : PR comment
		if : ${{ github.event.issue.pull_request }}

## ¿Cómo lanzar 'workflows' de forma manual con 'workflow dispatch'?
El 'workflow dispatch' te permite lanzar un 'workflow' de forma manual y agregar los parámetros que desees. Puedes crear 'inputs', y estos pueden ser de diferentes tipos, como una elección, un boolean, o un string.



## ¿Cómo programar eventos con el 'schedule'?
Finalmente, el 'trigger' 'schedule' te permite programar eventos que ocurran a intervalos regulares. Puedes especificar los minutos, la hora, el día del mes, el mes, y el día de la semana.

## ¿Cómo puedes practicar la creación de 'workflows' basados en 'triggers'?
Para practicar la creación de 'workflows', te recomiendo que crees un nuevo archivo 'workflow' que use al menos tres de los 'triggers' que acabamos de explicar.


