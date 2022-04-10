#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat 

#docker build -f TestDockerWebForms/Dockerfile -t  TestDockerWebForms .
FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019 AS builder  
WORKDIR C:\\Users\\engmo\\source\\repos\\TestDockerWebForms  
COPY . .  
RUN msbuild TestDockerWebForms.sln /t:WebPublish /p:Configuration=Release  /p:WebPublishMethod=FileSystem /p:publishUrl=c:\out




FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8-windowsservercore-ltsc2019 AS publish
ARG source
WORKDIR /inetpub/wwwroot
COPY --from=builder c:\\out .
