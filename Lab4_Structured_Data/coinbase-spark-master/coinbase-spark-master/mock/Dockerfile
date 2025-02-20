FROM ubuntu:20.04

# Copy the required files
COPY Mock.scala /
COPY Mock.scala /home

# Update, upgrade, and install dependencies in one step
RUN apt update -y && apt upgrade -y && \
    apt install -y curl && \
    curl -sSLf https://scala-cli.virtuslab.org/get | sh

# Use an absolute path for WORKDIR
WORKDIR /home

# Prepare Scala CLI environment and dependencies
RUN echo "println(1)" | /root/.cache/scalacli/local-repo/bin/scala-cli/scala-cli -S 3.0.2 - && \
    echo "//> using dep org.java-websocket:Java-WebSocket:1.5.2" | /root/.cache/scalacli/local-repo/bin/scala-cli/scala-cli -S 3.0.2 - && \
    echo "//> using dep org.slf4j:slf4j-simple:1.7.25" | /root/.cache/scalacli/local-repo/bin/scala-cli/scala-cli -S 3.0.2 -

# Set the entry point and default command
ENTRYPOINT ["/root/.cache/scalacli/local-repo/bin/scala-cli/scala-cli"]
CMD ["-S", "3.0.2", "Mock.scala"]
