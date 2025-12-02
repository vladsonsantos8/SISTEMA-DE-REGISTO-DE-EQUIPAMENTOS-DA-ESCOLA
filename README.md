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










<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <title>Sistema de Achados e Perdidos</title>
    <link rel="stylesheet" href="estilo.css">
</head>
<body>

    <div class="container-principal">

        <!-- Sidebar -->
        <aside class="barra-lateral">
            <h2 class="titulo-sistema">Achados & Perdidos</h2>

            <nav class="menu">
                <a href="#" class="item-menu">Dashboard</a>
                <a href="#" class="item-menu">Equipamentos</a>
                <a href="#" class="item-menu">Reivindicações</a>
                <a href="#" class="item-menu">Devoluções</a>
                <a href="#" class="item-menu">Configurações</a>
            </nav>
        </aside>

        <!-- Conteúdo -->
        <main class="conteudo">
            <h1 class="titulo-pagina">Resumo Geral</h1>

            <div class="area-cartoes">

                <div class="cartao">
                    <p class="descricao-cartao">Total de Equipamentos</p>
                    <h2 class="valor-cartao">32</h2>
                </div>

                <div class="cartao">
                    <p class="descricao-cartao">Equipamentos Reivindicados</p>
                    <h2 class="valor-cartao">7</h2>
                </div>

                <div class="cartao">
                    <p class="descricao-cartao">Equipamentos Devolvidos</p>
                    <h2 class="valor-cartao">19</h2>
                </div>

            </div>

        </main>

    </div>

</body>
</html>










body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f2f4f7;
}

.container-principal {
    display: flex;
    height: 100vh;
}

/* BARRA LATERAL */
.barra-lateral {
    width: 250px;
    background: #1e3a5f;
    color: white;
    padding: 20px;
}

.titulo-sistema {
    text-align: center;
    margin-bottom: 30px;
    font-size: 22px;
    font-weight: bold;
}

.menu {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.item-menu {
    color: white;
    text-decoration: none;
    padding: 10px;
    border-radius: 6px;
    transition: 0.3s;
}

.item-menu:hover {
    background: #2f548a;
}

/* CONTEÚDO PRINCIPAL */
.conteudo {
    flex: 1;
    padding: 40px;
}

.titulo-pagina {
    margin-bottom: 30px;
    font-size: 28px;
}

/* CARTÕES */
.area-cartoes {
    display: flex;
    gap: 25px;
}

.cartao {
    width: 250px;
    background: white;
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    text-align: center;
}

.descricao-cartao {
    font-size: 16px;
    color: #555;
}

.valor-cartao {
    font-size: 40px;
    color: #1e3a5f;
    margin-top: 15px;
}

