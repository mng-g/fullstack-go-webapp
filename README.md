Fullstack go webapp

**Backend**

mkdir $GOPATH/src/fullstack-go-live
cd $GOPATH/src/fullstack-go-live/
git init
echo "*node_modules" > .gitignore
touch compose.yaml
# fare curl da git che scarica un docker compose per postgres
docker compose up -d db
docker exec -it db psql -U postgres
	\l
	\dt
mkdir backend
cd backend
go mod init api
# install dependencies
go get github.com/gorilla/mux github.com/lib/pq
touch main.go go.dockerfile
...
cd ..
docker compose build
docker compose up -d goapp

==
TEST THE API!
==

**Frontend**

npx create-next-app@latest --no-git
cd frontend
npm i axios
npm run dev

touch .dockerignore next.dockerfile

docker compose build
docker compose up -d nextapp
