import requests
from bs4 import BeautifulSoup
import openai

def extract_info(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')
    
    # Aqui você deve adaptar a busca conforme a estrutura do site
    title = soup.find('title').get_text()
    description = soup.find('meta', attrs={'name': 'description'})['content']
    
    return title, description

def generate_article(company_name, description):
    prompt = f"Write a concise and informative article about {company_name}. Description: {description}"
    
    openai.api_key = 'YOUR_OPENAI_API_KEY'  # Substitua pela sua chave da API OpenAI
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo", 
        messages=[{"role": "user", "content": prompt}]
    )
    
    return response['choices'][0]['message']['content']

def main(url):
    title, description = extract_info(url)
    article = generate_article(title, description)
    return article

# Exemplo de uso
url = "https://example.com"  # Substitua pelo site da empresa que deseja pesquisar
print(main(url))
