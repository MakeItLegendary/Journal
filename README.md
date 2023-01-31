# Journal
App or Macro to keep a digital daily journal through OneNote on a Galaxy tablet

Create an application, app or macro, that takes a journal page template (based on the above info) and creates a new page in a digital journal that can be added to throughout the day. The original vision was a OneNote Notebook automation but further thoughts have been toward appending the pages to an annual pdf document. This could generalize the use and maybe give some extra permanence but would make follow-up and reuse of past entries for other activities trickier. 

### Flow/Layout
Action is taken to start the application (click shortcut, run exe...)

     : define variables
     
     set (LastDate, LastDay, LastMouth, LastYear, LastEntry,
             Today, Day, Mouth, Year)
     get Today =current date
          parse Today ( Day =day, Month =month, Year =year)
          
     : Need some persistent variables to remember
     :     - where and how the journal is kept (pdf, OneNote...) 
     :     - what the current page template is
     :     - owner information, password (?)
     
     set (LastRun, JournalLocaI, TemplateLocal, Owner)
     
     : find the date of the last entry
     : might be a persistent variable set at the last session
     : better to query the last file/database to check when it was last open
     : maybe both to alert that a day was missed (further action?)
     
     get LastEntry =last entry date;
            LastDate = persistent variable from The last instance/action
            
     : compare all the date variables to determine whether to open a new page/entry
     : or open the last entry ie. the last entry was created earlier on the current day 
     
          parse LastEntry ( LastDay =day, LastMonth =month, LastYear =year)
          if LastEntry =Today (
