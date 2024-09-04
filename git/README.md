# Configuring Git

## Settings
- **Name**: `git config --global user.name "Leonard Chi"`
- **Email**: `git config --global user.email "leonardocompsci@gmail.com"`
- **Default Editor**: `git config --global core.editor "code --wait"`
- **Line Ending**:

    `git config --global core.autocrlf input` (mac/linux)

    `git config --global core.autocrlf true` (windows)

## Level
- **System**: All users
- **Global**: All repositories of the current user
- **Local**: Current repository

## Access configuration settings
`git config --global -e`
