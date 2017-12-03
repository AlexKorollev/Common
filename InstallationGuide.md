# Check Style

1. npm install --save-dev jshint

2. Create a .jshintrc file which will contain your specific configuration

3. In package.json in scripts property add new property:
    
    "lint": "node_modules/.bin/jshint PATH_TO_FILE_OR_FOLDER"
    
4. To start checking - type command 'npm run lint'
  
