Using a linux app called Sublime Text will make the email headers easier to read.  

However the linux app called emlAnalyzer will allow you to not only view the headers easier but also can extract attachments without risk.

```session-shell 
emlAnalyzer -i Urgent\:.eml --header --html -u --text --extract-all
```


The above command will extract header information and text from the Urgent.eml file as well as attachments.

https://emailrep.io/

Will allow you to get the reputation of the email sender.

sha256sum filename.txt will give you a hash value that can be used in virustotal.com to see if any anti virus programs detect it.
The behavior tab will have more details about the virus.

https://labs.inquest.net/ is another site to evaluate the virus.  use the `INDICATOR LOOKUP` option to conduct hash-based analysis.
