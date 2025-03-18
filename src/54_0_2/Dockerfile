# Definicja wersji SDK, którą chcemy pobrać
ARG NEXO_VERSION="50_0_2"

FROM mcr.microsoft.com/windows/servercore:ltsc2022 AS builder
SHELL ["powershell", "-Command"]

# Metadane obrazu
LABEL maintainer="Mateusz <kontakt@piatek.dev>" `
      description="Obraz zawierający InsERT nexoSDK w wersji ${NEXO_VERSION}" `
      version="${NEXO_VERSION}"

# Instalacja 7-Zip do rozpakowywania archiwum SDK
RUN Invoke-WebRequest -Uri "https://www.7-zip.org/a/7z1900-x64.msi" -OutFile "7zip.msi"; Start-Process msiexec.exe -ArgumentList '/i 7zip.msi /quiet /norestart' -NoNewWindow -Wait; Remove-Item -Force 7zip.msi

# Pobranie InsERT nexoSDK
RUN $ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri "https://ftp.insert.com.pl/pub/aktualizacje/InsERT_nexo/nexoSDK_${NODE_VERSION}.exe" -OutFile "C:\\sdk.zip"

# Rozpakowanie SDK przy użyciu 7-Zip
RUN & 'C:\\Program Files\\7-Zip\\7z.exe' x C:\\sdk.zip -oC:\\sdk -y

# Usunięcie archiwum po rozpakowaniu
RUN Remove-Item -Force C:\\sdk.zip

# Zmiana nazwy folderu SDK na "nexoSDK"
RUN $firstFolder = Get-ChildItem -Path C:\sdk | Where-Object { $_.PSIsContainer } | Select-Object -First 1; if ($firstFolder) { Rename-Item -Path $firstFolder.FullName -NewName "nexoSDK" }


# Tworzenie finalnego obrazu
FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Kopiowanie nexoSDK do finalnego obrazu
COPY --from=builder C:\\sdk\\nexoSDK\\Bin C:\\InsertNexoSDK