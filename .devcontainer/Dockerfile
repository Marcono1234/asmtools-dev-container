# Based on https://github.com/microsoft/vscode-dev-containers/blob/master/containers/java/.devcontainer/Dockerfile

# Stage for building AsmTools
FROM openjdk:8 AS asmtools-build
# Install zip for SDKMAN and git for cloning AsmTools
RUN apt-get update && apt-get install -y zip git
# Download SDKMAN used for installing Ant
RUN curl -s "https://get.sdkman.io?rcupdate=false" | bash
# Make script executable
RUN chmod a+x "$HOME/.sdkman/bin/sdkman-init.sh"
# Clone AsmTools
RUN git clone https://github.com/openjdk/asmtools.git
# Install Ant and build AsmTools
# Use `bash`, default shell does not have `source`
RUN bash -c "source $HOME/.sdkman/bin/sdkman-init.sh && sdk install ant && cd asmtools/build && ant clean build"
RUN mkdir asmtools-build-results
# Move LICENSE, release file (contains information about build) and JAR to results directory
RUN cd asmtools-*-build/release/ && mv LICENSE /asmtools-build-results/ && mv release /asmtools-build-results/ && mv lib/asmtools.jar /asmtools-build-results/

# Build the final image
FROM mcr.microsoft.com/vscode/devcontainers/java:11
# Copy the AsmTools build results
COPY --from=asmtools-build /asmtools-build-results/ /usr/local/asmtools/
# Add custom bash scripts
COPY asmtools-scripts /usr/local/asmtools/scripts
# Change PATH environment variable to include bash scripts
ENV PATH="/usr/local/asmtools/scripts:$PATH"
