####How it works

#####Core Function



----------------------
![image](https://raw.githubusercontent.com/farruggio/Prova/master/HowTo/colora_checklist.png)

The colora function search the mutated genes and painting them in red or green according to mutation's level.
   
    
     function colora(list,graphics){
      for (i in list){ if (lis[i].FC >3){graphics.getNodeUI(lis[i].Symbol).color=0xFF0000} else
         if (list[i].FC>2){ graphics.getNodeUI(lis[i].Symbol).color=0xFF0055} else
            if (list[i].FC>1.5){ewe.getNodeUI(lis[i].Symbol).color=0xFF0099} else
              if (list[i].FC<-3){grapphics.getNodeUI(lis[i].Symbol).color=0x00FF00} else
                if (list[i].FC<-2){graphics.getNodeUI(lis[i].Symbol).color=0x00CD00} else
                  if (list[i].FC<-1.5){graphics.getNodeUI(lis[i].Symbol).color=0x008B00} else                                 						graphics.getNodeUI(lis[i].Symbol).color = 0xffffff}
  
      };



The Checklist function check if one node is selected and paint it in yellow.


    function checklist(nodeToLis,graphics){
        for (i in nodeToLis){
             graphics.getNodeUI(nodeToLis[i]).color=0xFFFF00;
        }
    } 
   
This two function are called every time that an events change (for example clicking one node)

-----------------------
![image](https://raw.githubusercontent.com/farruggio/Prova/master/HowTo/find_neighbors.png)


Them we have the function for find neighbors

		function alovic(nodeToLis){
          novadata=[ ];
          nei=[ ];
    
        
    //This step find neighbors for each node in nodeToLis and push them in nei array
    for (i in nodeToLis){
        vicini=funz.getNodeUI(nodeToLis[i]).node.links;
          for (i in vicini){ 
          nei.push(vicini[i].toId);
          nei.push(vicini[i].fromId) 
          }
    }
          
    //This function paint in yellow the neighbors of the nodes in nodeToLis array 
    nei = deleteDuplicati(nei)
    for (i in nei){
    funz.getNodeUI(nei[i]).color=0xffff00} 
    //Richiama funzione per eliminare duplicati , Colpa dei link multipli 
    


	//This function update the data in slickgrid
	for (item in data1.nodes)
	for (i in nei){
	{ if (data1.nodes[item].Symbol===nei[i]){novadata.push(data1.nodes[item])}	}}
	
	//This declaration permit to find second neighbors  
	vicvic=nei;

	renderer.resume()
	}
	
	
![image](https://raw.githubusercontent.com/farruggio/Prova/master/HowTo/find_second_nei.png)	
	
------------------------



Finally the new Graph function

    //This function is based on difference between all nodes (alpha variables) and the list of selected node

	function newGraph(data, list){

     var alpha=data1.nodes;
     var ausilio=[]
     for (i in alpha){ausilio.push(alpha[i].Symbol)}
     
     var diff = $(ausilio).not(list).get();
     for (i in diff)
        graph.removeNode(diff[i]);
     
    }	

![image](https://raw.githubusercontent.com/farruggio/Prova/master/HowTo/new_graph.png)
