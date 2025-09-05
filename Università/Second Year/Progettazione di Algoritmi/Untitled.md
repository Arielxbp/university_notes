```python
def es(G,v1,v2):
	distanza=[float("inf")]*len(G)
	coda=[]
	for s in v1:
		distanza[s]=0
		coda.append(s)
	i=0
	while len(coda)>i:
		u=coda[i]
		i+=1
		for v in G[u]:
			if distanza[v]==float("inf"):
				distanza[v]=distanza[u]+1
				coda.append(v)
	minimo=len(G)-1
	for nodov2 in v2:
		if distanza[nodov2]<minimo:
			minimo=distanza[nodov2]
	return minimo
```


```python
def es(G):
	visitati=[0]*len(G)
	cammino=[]
	def DFSr(u,G,padre,cammino):
		cammino.append(u)
		while G[u]: # finché esiste un nodo adiacente v al nodo u
			v=G[u].pop() # lo prendo
			if  v==padre and G[u]: # se il nodo v preso è il padre di u e nella lista di adiacenza di u c'è altro 
				vv=G[u].pop() # allora prendo l'altro
				G[u].append(v) # e rimetto il padre nella lista di adiacenza
			DFSr(v,G,u,cammino) # e quindi procedo con l'altro ( o se è rimasto solo il padre allora procedo con lui)
	DFSr(1,G,-1,cammino)
	return cammino
```

```python
def es(u,v,parole):
	n=len(parole[0])
	G=[[] for _ in range(len(parole))]
	for parola in parole:
		for confr in parole:
			diff=0
			for i in range(n):
				if parola[i]==confr[i]:
					diff+=1
			if diff==1:
				G[parola].append(confr)
	padre=[-1]*len(parole)
	padre[u]=u
	def DFSr(u,G, padre):
		for adia in G[u]:
			if padre[adia]==-1:
				padre[adia]=u
				DFSr(adia,G,padre)
	DFSr(u,G,padre)
	result=[]
	for parola in padre:
		if parola=v:
			while padre[parola]!=parola:
				result.append(parola)
				parola=padre[parola]
		break
	return result
```