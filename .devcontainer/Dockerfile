# Base image with Java (required for Android development)
FROM mcr.microsoft.com/devcontainers/java:21

# Install Android SDK dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    unzip \
    wget \
    lib32stdc++6 \
    lib32z1 \
    qemu-kvm \
    && rm -rf /var/lib/apt/lists/*

# Set up Android SDK
ENV ANDROID_HOME=/usr/local/android-sdk
ENV PATH=$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$PATH

RUN mkdir -p $ANDROID_HOME/cmdline-tools && \
    wget -q https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip -O /tmp/cmdline-tools.zip && \
    unzip /tmp/cmdline-tools.zip -d $ANDROID_HOME/cmdline-tools && \
    mv $ANDROID_HOME/cmdline-tools/cmdline-tools $ANDROID_HOME/cmdline-tools/latest && \
    rm /tmp/cmdline-tools.zip

# Accept Android SDK licenses
RUN yes | sdkmanager --licenses

# Set user permissions
RUN chown -R vscode:vscode $ANDROID_HOME
