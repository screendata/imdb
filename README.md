# imdb
source
import csv
from urllib.request import urlopen as uReq
from bs4 import BeautifulSoup as soup

my_url = "https://www.imdb.com/title/tt1477834/?pf_rd_m=A2FGELUUNOQJNL&pf_rd_p=740b2354-425b-4cd3-947b-7f9cb4349875&pf_rd_r=DHZY20J3YJNEKWHNGB0A&pf_rd_s=right-7&pf_rd_t=15061&pf_rd_i=homepage&ref_=hm_cht_t0"

uClient = uReq(my_url)
page_html = uClient.read()
uClient.close()
page_soup = soup(page_html, "html.parser")
title = page_soup.find("h1", {"class":""}).text
rating = page_soup.find("span", {"itemprop":"ratingValue"}).text
user_reviews = page_soup.findAll("span", {"itemprop":"reviewCount"})[0].text
critic_reviews = page_soup.findAll("span", {"itemprop":"reviewCount"})[1].text
language = page_soup.findAll("div", {"class":"txt-block"})[5].text
release = page_soup.findAll("div", {"class":"txt-block"})[6].text
country = page_soup.findAll("div", {"class":"txt-block"})[4].text
filming_location = page_soup.findAll("div", {"class":"txt-block"})[8].text
budget = page_soup.findAll("div", {"class":"txt-block"})[9].text
worldwide_gross = page_soup.findAll("div", {"class":"txt-block"})[10].text
production_company = page_soup.findAll("div", {"class":"txt-block"})[11].text
runtime = page_soup.findAll("div", {"class":"txt-block"})[13].text

filename = "movie.csv"
f = open(filename, "w")
headers = "Title, Rating, User Reviews, Critic Reviews, Language, Release Date, Country, Filming Locations, Budget, Worldwide Gross, Production Company, Runtime\n"
f.write("headers")

list = [('Title', print(title)), ('Rating', print(rating)), ('User Reviews', print(user_reviews)), ('Critic Reviews', print(critic_reviews)), ('Language', print(language)), ('Release Date', print(release)), ('Country', print(country)), ('Filming Location', print(filming_location)), ('Budget', print(budget)), ('Worldwide Gross', print(worldwide_gross)), ('Production Company', print(production_company)), ('Runtime', print(runtime))]

list[0] = title.strip()
list[1] = rating.strip()
list[2] = user_reviews.strip()
list[3] = critic_reviews.strip()
list[4] = language.strip()
list[5] = release.strip()
list[6] = country.strip()
list[7] = filming_location.strip()
list[8] = budget.strip()
list[9] = worldwide_gross.strip()
list[10] = production_company.strip()
list[11] = runtime.strip()

print(title)
print(rating)
print(user_reviews)
print(critic_reviews)
print(language)
print(release)
print(country)
print(filming_location)
print(budget)
print(worldwide_gross)
print(production_company)
print(runtime)

f.write(title + rating + user_reviews + critic_reviews + language + release + country + filming_location + budget + worldwide_gross + production_company + runtime)
