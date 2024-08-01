
```
#!/bin/bash

# Variables
REPO_URL="https://github.com/WWSYSTEM/test"
CLONE_DIR="/home/container/test"
REQUIREMENTS_FILE="requirements.txt"

# Check if the directory already exists
if [ ! -d "$CLONE_DIR" ]; then
	echo "Cloning the repository..."
	git clone https://${REPO_URL#https://} $CLONE_DIR
fi

	cd ${CLONE_DIR}
    git pull https://${REPO_URL#https://}
# Clone the repository
	

# Check if the clone was successful
if [ $? -eq 0 ]; then
    echo "Repository cloned successfully into $CLONE_DIR"
else
    echo "Failed to clone the repository"
fi

if [ ! -f "$REQUIREMENTS_FILE" ]; then
    echo "requirements.txt file not found!"
    exit 1
fi

# Install packages from requirements.txt
echo "Installing packages from $REQUIREMENTS_FILE..."
pip3 install -r $REQUIREMENTS_FILE

# Check if the installation was successful
if [ $? -eq 0 ]; then
    echo "All packages installed successfully."
else
    echo "Failed to install some packages."
    exit 1
fi
```
