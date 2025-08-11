## Build multi-stage para otimizar tamanho da imagem final
# -----------------------
# Etapa 1: Build — instalação das dependências e preparação do código
FROM node:current-alpine3.22 AS build

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia apenas os arquivos de manifesto do npm para instalação otimizada das dependências
COPY package*.json .
RUN npm install

# Copia o restante do código-fonte para o container
COPY . .


# -----------------------
# Etapa 2: Runtime — contém apenas o necessário para execução
FROM node:current-alpine3.22

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia dependências já instaladas e código da aplicação a partir da etapa de build
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app ./

# Cria um usuário não-root para reduzir riscos de segurança
RUN addgroup app && adduser -S -G app app
USER app

# Expõe a porta 8080 e define o comando de inicialização
EXPOSE 8080
CMD [ "node", "server.js" ]