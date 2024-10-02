1. A batch file that installs ot the user:
	1. Bun, by running: `powershell -c "irm bun.sh/install.ps1|iex"`
	2. TypeScript, by running: `bun add -g typescript`
	1. The tsmagic executable
2. tsmagic is an executable, that when run from a certain directory creates or overrides the files:
	1. tsconfig.json, with the content:
		```
		{
		    "compilerOptions": {
		        "target": "es2016",
		        "module": "commonjs",
		        "inlineSourceMap": true,
		        "esModuleInterop": true,
		        "forceConsistentCasingInFileNames": true,
		        "strict": true,
		        "noImplicitAny": true,
		        "strictNullChecks": true,
		        "strictFunctionTypes": true,
		        "strictPropertyInitialization": true,
		        "noImplicitThis": true,
		        "useUnknownInCatchVariables": true,
		        "alwaysStrict": true,
		        "exactOptionalPropertyTypes": true,
		        "noPropertyAccessFromIndexSignature": true,
		    }
		}
		```
	2. .vscode/settings.json, with the content:
		```
		{
		    "files.exclude": {
		        ".vscode": true,
		        "**/*.js": true,
		        "tsconfig.json": true
		    }
		}
		```
	3. .vscode/tasks.json, with the content:
		```
		{
		    "version": "2.0.0",
		    "tasks": [
		        {
		            "label": "Watch TS",
		            "command": "tsc --watch",
		            "isBackground": true,
		            "presentation": {
		                "reveal": "never",
		                "focus": false,
		                "panel": "dedicated",
		            }
		        }
		    ]
		}
		```
	4. and runs `tsc --watch`