# SISTEMA-DE-REGISTO-DE-EQUIPAMENTOS-DA-ESCOLA
 O Sistema de Registo de Equipamentos da Escola é uma aplicação simples desenvolvida para ajudar escolas a controlar os dispositivos existentes nas suas instalações, como computadores, impressoras, projetores e outros materiais.
O sistema foi criado devido ao problema frequente do desaparecimento de artigos e equipamentos, provocado pela falta de um controle organizado e atualizado.

A aplicação permite registar, listar, editar e apagar equipamentos de forma rápida, garantindo que a escola tenha um inventário claro e sempre disponível.

O projeto foi desenvolvido apenas com HTML, PHP e MySQL, tecnologias acessíveis, leves e adequadas ao nível médio de informática. O sistema funciona localmente, sem necessidade de internet, tornando-se ideal para escolas com poucos recursos tecnológicos.

Funciona off-line,é extremamente simples e direto(registro, consulta, editar) sem complicações, tecnologias acessíveis,

O sistema ajuda a:
	controlar quem mexe nos equipamentos
	saber onde cada item está
	evitar trocas, roubos
 
      Regras do projecto

1. Todo equipamento deve ter um registo único

Nenhum equipamento pode ser inserido sem os campos obrigatórios:
	•	nome
	•	tipo
	•	estado
	•	local

Isso garante que não existam itens sem identificação.

 2. O estado do equipamento deve ser sempre “Funcional” ou “Avariado”

O sistema só aceita estes dois estados.
Isto evita informações confusas (ex.: “mais ou menos”, “meio avariado”).

3. Nenhum equipamento pode ser apagado sem confirmação

Antes de eliminar um registro, o sistema deve perguntar:
“Tem certeza que deseja apagar este equipamento?”

Isso reduz erros e perda de dados importantes.

 4. O local (sala/setor) deve ser sempre definido ao cadastrar

O equipamento só pode ser registado se tiver um local.
Essa regra existe para combater o desaparecimento/ extravio de dispositivos.
A escola deve sempre saber onde cada dispositivo está.
 
  5. A data de registo deve ser automaticamente gerada

O sistema deve inserir a data do registo automaticamente no banco de dados.
O utilizador não precisa preencher esse campo.

6. Um equipamento avariado deve ser identificado para manutenção

Sempre que o estado for “avariado”, o sistema deve permitir identificar facilmente.
Exemplo: cor diferente ou alerta na listagem.
Isso ajuda no trabalho do técnico de informática.

 7. Não pode haver dois equipamentos com o mesmo nome + local

Exemplo:
Dois registos com “Computador 01 – Sala 5” não são permitidos.
Isso evita duplicações e confusão no inventário.

 8. O sistema deve mostrar todos os equipamentos em tabela organizada
A listagem deve permitir ao usuário visualizar rapidamente:
	•	nome
	•	tipo
	•	estado
	•	local
	•	data do registo
 9. O sistema deve funcionar totalmente offline

Não pode depender de internet ou servidores externos.
A escola deve conseguir usar apenas com HTML + PHP + MySQL no computador local.

	  1. Paleta Profissional (Azul + Cinza)

Recomendada para sistemas escolares e administrativos.
	•	Azul principal: #1A73E8
	•	Azul claro (hover): #4D9FFF
	•	Cinza claro (fundo): #F4F6F8
	•	Cinza médio (borda/linhas): #D0D4D8
	•	Preto suave (texto): #333333
	•	Verde (funcional): #34A853
	•	Vermelho (avariado): #EA4335

- limpa
- profissional
- moderno
-  combina com sites escolares 

Modelação em caso de uso 

Atores
	•	Administrador (Direção da escola ou funcionário autorizado)
	•	Usuário Comum (Estudantes, professores, funcionários)

(Use case)UC01 – Registrar Item Encontrado
Ator: Administrador
Descrição: O administrador regista um objeto encontrado, insere descrição, categoria, local e foto.

UC02 – Consultar Itens Encontrados
Ator: Usuário
Descrição: O usuário pode ver a lista de itens encontrados.

UC03 – Pesquisar Item por Categoria
Ator: Usuário
Descrição: O usuário pode filtrar itens (ex: telemóveis, mochilas, cadernos).

UC04 – Reclamar Item (Solicitar Devolução)
Ator: Usuário
Descrição: O usuário clica num item e solicita devolução preenchendo nome e contacto.

UC05 – Validar Reivindicação
Ator: Administrador
Descrição: O administrador confirma se o item pertence ao solicitante.

UC06 – Entregar Item e Marcar como Devolvido
Ator: Administrador
Descrição: O administrador marca o item como devolvido e o sistema arquiva.

Normalização do banco de dados

 1FN – Primeira Forma Normal

Regras:
	•	Dados atómicos
	•	Sem repetições
	•	Cada campo um valor único

Resultado:
	•	Separar itens e reclamações.

⸻

Tabelas após 1FN

itens
	•	id_item
	•	descricao
	•	categoria
	•	local_encontrado
	•	data_registro
	•	foto
	•	status

reclamacoes
	•	id_reclamacao
	•	id_item (FK)
	•	nome_reclamante
	•	contato_reclamante
	•	data_reclamacao

⸻

2FN(forma normal) – Segunda Forma Normal

Regras:
	•	Nenhum atributo depende parcialmente da chave.

➡ As dependências já estão corretas.
Sem alterações.

⸻

 3FN – Terceira Forma Normal

Regras:
	•	Remover dependências transitivas.


