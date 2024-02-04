Q1.	Create a directory named "MyFiles" in your home directory. Navigate into this directory and list its contents.

Ans.  mkdir ~/MyFiles
cd ~/MyFiles
ls


Q2.	Copy a file named "document.txt" from your home directory to the "MyFiles" directory. Move the file to a subdirectory named "Documents" within "MyFiles."

Ans. cp ~/document.txt ~/MyFiles/
mv document.txt Documents/


Q3.	Create an empty file named "notes.txt" in the "MyFiles" directory. Afterward, delete the file.

Ans. touch notes.txt
rm notes.txt

Q4.	Create a hard link named "hardlink.txt" for the file "document.txt" within the "Documents" subdirectory. Also, create a symbolic link named "symlink.txt" in the same location.

Ans. ln ~/MyFiles/Documents/document.txt ~/MyFiles/Documents/hardlink.txt
ln -s ~/MyFiles/Documents/document.txt ~/MyFiles/Documents/symlink.txt


Q5.	In the "MyFiles" directory, use a single command to list all files that start with the letter "a" and have a ".txt" extension.

Ans.  ls ~/MyFiles/a*.txt

Q6.	Rename all files in the "Documents" subdirectory of "MyFiles" with a ".bak" extension. Ensure the original file names are preserved.

Ans. cd ~/MyFiles/Documents
for file in *; do mv "$file" "${file%.txt}.bak"; done

Q7.	Use a wildcard character to copy all files from the "Documents" subdirectory of "MyFiles" to another directory named "Backup."

Ans. cp ~/MyFiles/Documents/* ~/Backup/

Q8.	Execute the ls command to list files in the current directory. Save the output to a file named "file_list.txt." Then, use a pipe to filter the output through grep to display only files with a ".txt" extension.

Ans. ls > file_list.txt
ls | grep '\.txt$' >> file_list.txt

Q9.	Create a new text file named "my_notes.txt" using the touch command. Open the file in the Vim editor, add some text, and save the changes.

Ans. touch my_notes.txt
vim my_notes.txt  

Q10.	Run the date command and store the output in a variable named "current_date." Display the value of the variable and append it to the "my_notes.txt" file.

Ans.  current_date=$(date)
echo $current_date >> my_notes.txt

Q11.	Edit the Bash startup script (e.g., .bashrc) to set an environment variable named "CUSTOM_PATH" to a specific directory path. Ensure the variable is available in new shell sessions.

Ans.  echo 'export CUSTOM_PATH="/your/specific/directory"' >> ~/.bashrc
source ~/.bashrc

Q12.	Use the echo command to add a new line of text to the "my_notes.txt" file without overwriting existing content. Verify that the new text is appended.

Ans.  echo 'New line of text' >> my_notes.txt

Q13.	List all files in the "/etc" directory, filter the output to include only those containing the word "conf," and save the result to a file named "conf_files.txt."

Ans. ls /etc | grep 'conf' > conf_files.txt
Q14.	Open the "my_notes.txt" file in Vim. Use Vim's search and replace functionality to replace all occurrences of the word "important" with "critical." Save the changes.

Ans. vim my_notes.txt

Q15.	Create a new user account named "john_doe." Set the user's home directory to "/home/john_doe" and assign the user to the "users" group.

Ans. sudo adduser john_doe --home /home/john_doe --ingroup users

Q16.	Add the user "john_doe" to the sudoers file, allowing them superuser privileges. 
Confirm that "john_doe" can execute commands with sudo.

Ans. sudo usermod -aG sudo john_doe
sudo su - john_doe  

Q17.	Modify the user account "john_doe" to change the default shell to "/bin/bash" and set the account's expiration date to one month from today.

Ans. sudo usermod --shell /bin/bash --expiredate $(date -d "+1 month" +"%Y-%m-%d") john_doe

Q18.	Create a new group named "development_team." Add "john_doe" to this group and verify the group's existence.

Ans. sudo addgroup development_team
sudo usermod -aG development_team john_doe
getent group development_team

Q19.	Remove "john_doe" from the "users" group and add them to the "development_team" group. Confirm the changes.

Ans. sudo deluser john_doe users
sudo usermod -aG development_team john_doe
groups john_doe 

Q20.	Delete the user account "john_doe" and ensure that their home directory is also removed.

Ans. sudo deluser john_doe --remove-home

Q21.	Delete the group "development_team" and ensure that all users previously belonging to the group are appropriately handled.

Ans. sudo delgroup development_team

Q22.	Implement a password policy that requires users to change their passwords every 90 days. Apply this policy to all existing and new user accounts.

Ans. sudo chage -M 90 username

Q23.	Manually lock the user account "john_doe." Attempt to log in as "john_doe" to confirm that the account is locked. Then, unlock the account.

Ans. sudo passwd -l john_doe  
sudo su - john_doe
sudo passwd -u john_doe 

Q24.	Use the id command to display detailed information about the "john_doe" user, including user ID, group ID, and supplementary groups.

Ans. id john_doe

Q25.	Configure the password aging for the user "john_doe" to enforce a maximum password age of 60 days. Confirm that the changes take effect.

Ans. sudo chage -M 60 john_doe

