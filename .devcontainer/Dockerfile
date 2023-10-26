FROM mcr.microsoft.com/dotnet/sdk:7.0

RUN dotnet workload install maui-android

RUN apt update && apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    openjdk-11-jdk \
    && curl -fsSL https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -o packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb

RUN apt-get update && apt-get install -y unzip lib32stdc++6 lib32z1
RUN mkdir -p /usr/local/android-sdk
RUN wget -O /tmp/sdk-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-7302050_latest.zip
RUN unzip /tmp/sdk-tools.zip -d /usr/local/android-sdk
RUN echo y | /usr/local/android-sdk/cmdline-tools/bin/sdkmanager --sdk_root=/usr/local/android-sdk "platform-tools" "platforms;android-31"

ENV ANDROID_HOME /usr/local/android-sdk
ENV PATH $PATH:$ANDROID_HOME/platform-tools