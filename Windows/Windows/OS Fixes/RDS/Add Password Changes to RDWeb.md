RDS adding password change to web page:

iis manager
RDWeb
pages
application settings
change password change enable to true

then
%windir%\web\rdweb\pages

login.aspx
edit
find 
userpass
add after last /tr

<tr>
<td align="right">
<a href="password.aspx" target="_blank">Click here</a> to reset your password.
</td>
</tr>
