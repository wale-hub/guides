
#                           rsync

> *from Learn Linux TV*

>> *How to Use the rsync Command to Transfer Files*

>> *<https://www.youtube.com/watch?v=KG78O53u8rY>*

### Basic command
> `rsync sourceDIR targetDIR` 

## NOT a bi directional sync
Its a one directional sync/backup & targetDIR can have other stuff

* Can do file
  > - `rsync fileX targetDIR/fileX`
  > - `rsync fileX targetDIR/fileZ`

* Can use to copy files like cp
  > - `rsync file newFile`

* Can back over network
  > - `rsync sourceDIR address:targetDIR`

* Use verbose -v so you know whats happening
  > - `rsync -v sourceDIR targetDIR`

* For directories with subfiles use recursive -R
  > -  `rsync -vR sourceDIR targetDIR`
  > - REMEMBER `dir` means the dir folder and `dir/` means everything<br>
      inside/under the dir folder. If you copy to or from a `dir` you<br>
      are copying the dir folder as well, on the other hand, using<br>
      `dir/` means you are copying everything UNDER the dir folder (to<br>
      or from). 

## Dry run
Always do a dry run (test). Dry run is basically demo mode and it<br>
doesn't actually transfer but checks relevant parameters
  > * `rsync -Rv --dry-run sourceDIR targetDIR`

## Main sync/backup commands
* Archive mode `-a` copies over the meta data from the source
  > - `rsync -Rva sourceDIR tagetDIR`

* Using rsync as backup can create wierd situations whare if a file<br>
  name changes in the source dir then the target dir will have 2<br>
  relevant files, one with the old name (AND CONTENT) and other with<br>
  new name. One way to deal with this is with `--delete` option that<br>
  deletes *ANY* file in targetDIR that is not in sourceDIR: 
  > - `rsync -Rva --delete sourceDIR targetDIR`

* You can also remove the files from source dir after transferring to<br>
  target dir (basically like a mv command)
  > - `rsync -rva --remove-source-files sourceDIR targetDIR`

