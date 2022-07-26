---
title: "July 26, 2022, Day29"
output: 
  html_document:
    toc: true
    toc_float: true
    keep_md: true
date: '2022-07-26 08:22:22'
---

# 7.26(금) 크롤링 복습
## KBO 보도자료를 예시로 함

import requests 
from bs4 import BeautifulSoup

def crawling(soup):
  ul = soup.find("ul", class_ = 'boardPhoto')

  result = []
  links = []
  for div in ul.find_all("div", class_ = "txt"):
        result.append(div.find("a").get_text())
        links.append(div.find("a")['href'])
  return result, links


def main():

  url = "https://www.koreabaseball.com/News/BreakingNews/List.aspx"
  req = requests.get(url)
  soup = BeautifulSoup(req.text, "html.parser")

  print(crawling(soup))

if __name__ == "__main__":
  main()