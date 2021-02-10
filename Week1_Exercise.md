#1 
years = list(data['year'].unique())
years
len(years)
#there are 12 years and they are: 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997, 2002, 2007

#2
print(data.columns)
pop = data['pop'].max()
print(pop)

temp = data[data['pop']==pop]
temp

#It occurred in Asia China in 2007

#3

europe = data[data['continent'] == 'Europe']
sm_pop = europe[(europe['pop'] == europe['pop'].min()) & (europe['year'] == int('1952'))]
pop07 = europe[(europe['year'] == int('2007'))& (europe['country']== 'Iceland')]

sm_pop
#iceland had the smallest population in 1952

pop07
#iceland's population in 2007 was 301931
