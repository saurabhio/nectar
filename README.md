# nectar
Some useful commands, codes, etc.


### MongoDB
mongodump /h abc.def.mongolab.com /port 46719  /u username /p password123  /d dbname /o e:\MongodbBackup
mongodump -d dbname -o e:\MongodbBackup

mongorestore e:\MongodbBackup
mongorestore --db dbname E:\path\to\database\backup

mongoexport --db dbname --collection clname --type=csv --fieldFile fields.txt --out clname.csv
mongoexport --db dbname --collection clname --type=json --fieldFile fields.txt --out clname.json --pretty

bsondump --outFile abc.json abc.bson
mongoimport -d dbname -c clname abc.json

### Miniconda
conda install -y pip numpy scipy pandas scikit-learn matplotlib seaborn plotly nltk Pillow jupyter
conda install -y tensorflow keras

