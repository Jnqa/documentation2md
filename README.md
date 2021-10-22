# Create Documentation and save as .md file
A GitHub action to create a md file for your repository from files with using [XML Documentation Comments](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/).

## Usage

```yml
    - uses: actions/checkout@v2
    - name: Setup Node.js
      uses: actions/setup-node@v1
      with:
        node-version: '12.x'
      # Make changes here
    - name: MakeMD
      uses: Jnqa/documentation2md@v1
      id: makemd
      with:
        inputdir: test
        mdpath: docs
        mdname: messages.md
```

### Action inputs

| Name | Description | Default |
| --- | --- | --- |
| `inputdir` | Documentation files directory using [XML documentation comments](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/). | `-` |
| `mdpath` | Path to save md file. | `docs` |
| `mdname` | MD filename. | `messages.md` |

Аfter executing the action, a file will be created in the specified directory. next step you can apply it
(e.g. /docs/messages.md)

### Action outputs

| Name | Description | Example |
| --- | --- | --- |
| `mdfile` | Path to md file | `/docs/messages.md` |


```yml
      # Use it as you want
    - name: ReadMD
      run: |
        cat ${{ steps.makemd.outputs.mdfile }}
```

