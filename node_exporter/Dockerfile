FROM microsoft/windowsservercore

MAINTAINER Thiago Gonzaga <thiago.gonzaga@aurea.com>

RUN powershell Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force

RUN powershell Install-Module -Name 7Zip4Powershell -Force

RUN powershell New-Item -Type Directory C:\\node_exporter

RUN powershell Invoke-WebRequest -Uri https://github.com/prometheus/node_exporter/releases/download/v0.13.0/node_exporter-0.13.0.windows-amd64.tar.gz -OutFile C:\\node_exporter\\node_exporter-0.13.0.windows-amd64.tar.gz

RUN powershell Expand-7zip C:\\node_exporter\\node_exporter-0.13.0.windows-amd64.tar.gz C:\\node_exporter

RUN powershell Expand-7zip C:\\node_exporter\\node_exporter-0.13.0.windows-amd64.tar \"C:\\Program Files\"

WORKDIR C:\\Program\ Files\\node_exporter-0.13.0.windows-amd64

ENTRYPOINT ["node_exporter.exe"]

EXPOSE 9100