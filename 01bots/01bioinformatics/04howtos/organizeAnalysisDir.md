# Organize Analysis Directory

```bash
├── data
│   ├── external
│   ├── processed
│   └── raw
├── .gitignore
├── README.md
├── results
└── src
```

Some rules

- Most of the stuff happens in data. Whatever is the inhouse raw data goes in data/raw. Anything like annotations references and other supplementary files go in external. Anything that is done on that data which is not final and will no be used as a results file or a plot goes directory wise in processed. 

- All notes about the analysis go in README.md

  