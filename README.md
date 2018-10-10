# utl-modify-existing-master-table-using-transaction-table
Nice example of modify existing master table using transaction table.
    Nice example of modify existing master table using transaction table                                              
                                                                                                                      
    No need for an additional output table.                                                                           
                                                                                                                      
    github                                                                                                            
    https://tinyurl.com/y87pruag                                                                                      
    https://github.com/rogerjdeangelis/utl-modify-existing-master-table-using-transaction-table                       
                                                                                                                      
    SAS Forum                                                                                                         
    https://tinyurl.com/ybkxlopm                                                                                      
    https://communities.sas.com/t5/SAS-Programming/update-a-table-with-the-another-subselect/m-p/502942               
                                                                                                                      
                                                                                                                      
    INPUT                                                                                                             
    =====                                                                                                             
     WORK.MASTER total obs=4                                                                                          
                                                                                                                      
       ID1  ID2    A     B     C                                                                                      
                                                                                                                      
        1   10    X1    --    --                                                                                      
        2   20    Y1    Y2    Y3                                                                                      
        3   30    --    --    --                                                                                      
        4   40    R1    R2    R3                                                                                      
                                                                                                                      
                                                                                                                      
     WORK.TRANSACTION total obs=3                                                                                     
                                                                                                                      
      ID1  ID2    A     B     C                                                                                       
                                                                                                                      
       1    10    X1    X2    X3                                                                                      
       2    20    Y1    Y2    Y3                                                                                      
       3    30    Z4    Z5    Z6                                                                                      
                                                                                                                      
                                                                                                                      
    EXAMPLE UPDATED MASTER                                                                                            
    ----------------------                                                                                            
                                                                                                                      
     WORK.MASTER total obs=4                                                                                          
                                                                                                                      
     ID1  ID2    A     B     C                                                                                        
                                                                                                                      
      1    10    X1    X2    X3   => X2 and X3 replace '--'                                                           
      2    20    Y1    Y2    Y3                                                                                       
      3    30    Z4    Z5    Z6   => Z4.Z5 and Z6  replae '--'                                                        
      4    40    R1    R2    R3                                                                                       
                                                                                                                      
                                                                                                                      
    PROCESS                                                                                                           
    =======                                                                                                           
                                                                                                                      
    data master ;                                                                                                     
      modify master transaction;                                                                                      
      by id1 id2;                                                                                                     
    run;quit;                                                                                                         
                                                                                                                      
                                                                                                                      
    OUTPUT                                                                                                            
    ======                                                                                                            
    see above                                                                                                         
                                                                                                                      
                                                                                                                      
    *                _               _       _                                                                        
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _                                                                 
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |                                                                
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |                                                                
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|                                                                
                                                                                                                      
    ;                                                                                                                 
                                                                                                                      
    data master;                                                                                                      
    input id1 id2 a $ b $ c $;                                                                                        
    cards4;                                                                                                           
     1 10 X1 -- --                                                                                                    
     2 20 Y1 Y2 Y3                                                                                                    
     3 30 -- -- --                                                                                                    
     4 40 R1 R2 R3                                                                                                    
    ;;;;                                                                                                              
    run;quit;                                                                                                         
                                                                                                                      
                                                                                                                      
    data transaction;                                                                                                 
    input id1 id2 a $ b $ c $;                                                                                        
    cards4;                                                                                                           
     1 10 X1 X2 X3                                                                                                    
     2 20 Y1 Y2 Y3                                                                                                    
     3 30 Z4 Z5 Z6                                                                                                    
    ;;;;                                                                                                              
    run;quit;                                                                                                         
                                                                                                                      
