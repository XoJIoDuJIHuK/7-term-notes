- Создайте файл `service.proto` со следующим содержимым:
```proto
syntax = "proto3";  
  
package example;  
option go_package = "generated/;example";  
  
service Greeter {  
  rpc Add (Parm2Request) returns (Parm2Result);  
  rpc Mul (Parm2Request) returns (Parm2Result);  
  rpc Sub (Parm2Request) returns (Parm2Result);  
  rpc Div (Parm2Request) returns (Parm2Result);  
  rpc Pow2 (Parm1Request) returns (Parm1Result);  
  rpc ReallyHeavyFunction (Parm2Request) returns (Parm1Result);  
}  
  
message Parm2Request {  
  int32 x = 1;  
  int32 y = 2;  
}  
  
message Parm1Request {  
  int32 x = 1;  
}  
  
message Parm2Result {  
  int32 x = 1;  
  int32 y = 2;  
  int32 z = 3;  
}  
  
message Parm1Result {  
  int32 x = 1;  
  int32 z = 2;  
}
```
- Сервер
	- Создайте папку для сервера: `mkdir grpc-server && cd grpc-server`
	- Установите необходимые пакеты: `apt update && apt install -y golang-go protobuf-compiler ca-certificates && apt clean && rm -rf /var/lib/apt/lists/*`
	- Установите переменные окружения: `export GOPATH=/go && export PATH=$PATH:$GOPATH/bin`
	- Инициализируйте модуль Go: `go mod init go-grpc-server`
	- Установите необходимые пакеты Go: `go get google.golang.org/grpc && go get google.golang.org/protobuf && go install google.golang.org/protobuf/cmd/protoc-gen-go@latest && go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest`
	- Скопируйте файл `service.proto` в папку:
- Клиент