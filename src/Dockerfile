## Utilizando Multi-Stage Build
# Primeira Etapa: Instalando as dependências 
FROM node:current-alpine3.22 AS build

# Criando o diretório de trabalho
WORKDIR /app

# Copiando apenas os arquivos de dependência para instalar as dependências
COPY package*.json .
RUN npm install

# Após instalar as dependências copiar o restante da aplicação
COPY . .


# Segunda Etapa: Captura o essencial para a aplicação executar somente
FROM node:current-alpine3.22

# Criando o diretório de trabalho
WORKDIR /app

# Copia apenas os módulos do node e código necessário para a aplicação
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app ./

# Criando um usuário não root para evitar falhas de segurança deixando o usuário do container com menos permissões
RUN addgroup app && adduser -S -G app app
USER app

# Expor a porta de acesso 8080 e executar o comando de inicialização da aplicação
EXPOSE 8080
CMD [ "node", "server.js" ]