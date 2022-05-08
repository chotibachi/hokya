# hokya
Aim: Implementation of Classification algorithm in R Programming. (A)/n
Consider the annual rainfall details at a place starting from January 2012. We create an R time series object
for a period of 12 months and plot it.
Get the data points in form of a R vector

rain <-c(800,178,90,600,650,89,200,598,76,300,55,890,98,798,54,100,760,11,546,98)
print(rain)
timeseries <-ts(rain, start=c(2014,3),frequency=12)
print(timeseries)
plot(timeseries)


ts(constant,start=c(year,month), frequency=12)

Aim:Decision Tree. (B)

install.packages("party")
library(party) 
head(readingSkills)
i<-readingSkills[c(1:105),]
o<-ctree(nativeSpeaker~age+score+shoeSize, data=i)
plot(o)



Aim: perform the clustering using clustering algorithm.
n<-iris
n$Species<-NULL
(kc <-kmeans (n,3))
table(iris$Species,kc$cluster)
plot(n[c("Sepal.Length","Sepal.Width")],col=kc$cluster)


Aim: Practical Implementation of Linear Regression using R Tool.
a<-c(21,54,77,86,34,90,77,13,54)
b<-c(76,33,76,12,44,76,98,21,67)
relation<-lm(b~a)
print(relation)
print(summary(relation))
x<-data.frame(b=70)
result<-predict(relation,x)
print(result)
png(file="linear2.png")
plot(b,a,col="blue",main="height and width relation",abline(lm(a~b)),cex=1.3,pch=16,xlab="Width in
+ kg",ylab="Height in cm")
dev.off()
