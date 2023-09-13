import pandas as pd
import random

source_file = "SDW2023.csv"  
df_source = pd.read_csv(source_file, header=None, names=['Nome'], encoding='ISO-8859-1')

#Transformação
def generate_motivational_message(name):
    messages = [
        f"Olá, {name}! Lembre-se de que cada novo dia é uma oportunidade para brilhar e alcançar seus objetivos.",
        f"{name}, o caminho para o sucesso é construído um passo de cada vez. Continue avançando!",
        f"Seja persistente, {name}. Grandes realizações exigem tempo e esforço, mas você está no caminho certo.",
        f"{name}, sua determinação é inspiradora. Continue trabalhando duro para alcançar seus sonhos."
    ]
    return random.choice(messages)

df_transformed = df_source.copy()
df_transformed['Mensagem Motivadora'] = df_source['Nome'].apply(generate_motivational_message)

#Load
destination_file = "dados_usuarios_com_mensagens.csv"
df_transformed.to_csv(destination_file, index=False)

print("Mensagens motivadoras geradas e salvas.")

