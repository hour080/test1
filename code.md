import requests
import re
from bs4 import BeautifulSoup

a=[]
b=[]
c=[]
d=[]
e=[]
f=[]
g=[]



url='https://piao.qunar.com/ticket/list.htm?keyword=%E4%B8%89%E4%BA%9A&region=&from=mpl_search_suggest&page=1'
for i in range(1,6):
   new_link= re.sub('page=\d+','page=%d'%i,url,re.S)
   c.append(new_link)
j=0
while j<5:
    r=requests.get(c[j])
    if r.status_code==200:
       r.encoding = 'utf-8'
       html=r.text
       soup = BeautifulSoup(html,"html.parser")
       for link in soup.find_all('h3',class_="sight_item_caption"):
           a.append(link.get_text())
       for link in soup.find_all('span',class_="sight_item_price"):
            b.append(link.get_text())
       for link in soup.find_all('span',class_="product_star_level"):
           d.append(link.get_text())
       for link in soup.find_all('td',class_="sight_item_sold-num"):
           e.append(link.get_text())
       for link in soup.find_all('p',class_="address color999"):
           f.append(link.get_text())       
    j=j+1
   
k=0
while k<len(b):
    g.append(a[k]+"   "+f[k][:-2]+"\n"+b[k]+"   "+d[k]+"   "+e[k]+"\n")
    print(g[k])
    k=k+1   
m=0
p=[]
while m<len(b):
   h=[]
   
   h.append(a[m])
   h.append(f[m][:-2])
   h.append(b[m][1:-2])
   h.append(d[m][3:])
   h.append(e[m][4:])
   p.append(h)
   m=m+1
#按月销售量排序后的数组
p.sort(key=lambda s:int(s[4]),reverse=False)
fout=open("s.txt","w",encoding = 'utf-8')
for i in range(len(p)):
   fout.write(str(p[i])+'\n')   
fout.close()

#按价格排序后的数组
p.sort(key=lambda s:float(s[2]),reverse=True)
fi=open("g.txt","w",encoding = 'utf-8')
for i in range(len(p)):
   fi.write(str(p[i])+'\n')   
fi.close()
#综合排序
p.sort(key=lambda s:float(s[4])*float(s[3])/float(s[2]),reverse=True)
fli=open("pl.txt","w",encoding = 'utf-8')
for i in range(len(p)):
   if(float(p[i][3])==0.0):
      fli.write("")
   else:
      fli.write(str(p[i])+'\n')   
fli.close()



