# Introduction
This Documentation will cover the general use cases of finalized templates and ways to adapt them and assets that are usable.

Topic Covered:

- Installation and Dependancies
- Setup
- Template Codes
- Inserting Templates

## Structure Example.

 Template Explanation :
	 Full explanations of the current config of the templates and the usages they intend to serve
Tools And Assets:
	Tools:
		Templates that are designed to be called inside a written document
		Indicated by the Preface `T1_` to make it easier to search for whilst using the keyboard shortcut `CTRL+Shift+T`
	Assets
		Documentation on how to use specific templates and adapt them as needed
		Indicated by the Preface `T0_` To make it clear that these aren't functional tools to use.

The T1 preface can be used to find things quickly in search view or when inserting templates.
The T0 preface can be used to read documentation.

```
>Docs
	>Template Explanation
		>T0_Daily Note.md (covers the usage of the document and template usecase)
		>...
		
	>Assets
		>Dataview
			>DataviewReadme.md
			>T0_create a Dataview for Files modified
			>T0_GroupBy Error - Getting a Count
				
		>Templater
			>Moment.js
				>T0_Date interpertation
				>T0_Handeling Durations
					
			>Default Templater Commands
				>T0_
				
>Templater
	>Tools (Usable template with an explanation above it)
			>File
				>Frontmatter (FrontMatter copies for all full templates)
				>Body (Body Copies of all templates)
					>T1_Quote_body.md (take title of the file and convert it into a quote)
			>DataView
				>T1_Files Modified in Period.md 
				>T1_File Created in Period.md
				
			> Templater
				CurrentFile.md
			> TemplaterJS
				>Output Current Age in Weeks and Days.md
				>Total Value for Tag #Done.md
				>Link CurrentFile Period to Previous Period.md
				
	Other Templates
	...
```

# Installation
