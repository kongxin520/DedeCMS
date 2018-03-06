# DedeCMS
DedeCMS 5.7 Bug      

> [Suggested description] 
> DedeCMS 5.7 allows remote attackers to discover the full path via a direct request for include/downmix.inc.php or inc/inc_archives_functions.php.           
>
> ------------------------------------------
>
> [Additional Information]     
> Fix suggestions:              
> Modify the application source code to avoid information leakage.             
>
> The vulnerability was discovered by downloading the program's source code to local and online deployment tests.           
>
> Location: include/downmix.inc.php        
>
> Code:           
>
> helper('downmix');       
>
> Rows:13             
>
> Return error :       
>
> Fatal error: Call to undefined function helper() in /www/include/downmix.inc.php on line 13      
>
> Harm:     
>
> Web site physical path leakage .            
>
> conditions for execution:     
>
> Normal access can        
>
> Edition:      
>
> DedeCMS 5.7            
>
> Cause the cause :     
>
> Call to undefined function helper(),  cause path leakage     
>
> POC : http://127.0.0.1/include/downmix.inc.php        
>
>
>
>
>
>
> Location: /dede/inc/inc_archives_functions.php        
>
> Code:                       
>
> require_once(DEDEINC.'/dedehttpdown.class.php');              
>
> Rows:11      
>
> Return error :         
>
> Notice: Use of undefined constant DEDEINC - assumed 'DEDEINC' in /www/dede/inc/inc_archives_functions.php on line 11   
> Warning: require_once(DEDEINC/dedehttpdown.class.php): failed to open stream: No such file or directory in /www/dede/inc/inc_archives_functions.php on line 11    
> Fatal error: require_once(): Failed opening required 'DEDEINC/dedehttpdown.class.php' (include_path='.;C:\php\pear') in /www/dede/inc/inc_archives_functions.php on line 11     
>
> Harm:   
>
> Web site physical path leakage .    
>
> conditions for execution:            
>
> Normal access can                   
>
> Edition:               
>
> DedeCMS 5.7              
>
> Cause the cause :       
>
> require_once(): Failed opening required 'DEDEINC/dedehttpdown.class.php' (include_path='.;C:\php\pear') , cause path leakage     
>
> POC : http://127.0.0.1/dede/inc/inc_archives_functions.php       
>
> ------------------------------------------
>
> [VulnerabilityType Other]        
> Physical path leaks        
>
> ------------------------------------------
>
> [Vendor of Product]            
> dedecms            
>
> ------------------------------------------
>
> [Affected Product Code Base]      
> dedecms - 5.7       
>
> ------------------------------------------
>
> [Affected Component]       
> downmix.inc.php , Call to undefined function helper() , Web site physical path leakage         
>
> ------------------------------------------
>
> [Attack Type]        
> Remote       
>
> ------------------------------------------
>
> [Impact Information Disclosure]        
> true      
>
> ------------------------------------------
>
> [Attack Vectors]        
> The vulnerability can be triggered by visiting the URL below:           
> http://127.0.0.1/include/downmix.inc.php                 
> http://127.0.0.1/dede/inc/inc_archives_functions.php      
>
> ------------------------------------------
>
> [Discoverer]       
> kongxin           
