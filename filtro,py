    #   Interfaz

import streamlit as st
from PIL import Image

    #   Visualización de Datos 

import numpy as np
import pandas as pd

    #   API

logo_icono = Image.open(r'Adjuntos\Logo_solo.png')
logo_normal = Image.open(r'Adjuntos\YJB_Logo.png')

# logo_icono = Image.open(r'C:\Users\Cesar\Desktop\YJB\Biomecánica\Miscelaneo\Logo_solo.png')
# logo_normal = Image.open(r'C:\Users\Cesar\Desktop\YJB\Biomecánica\Miscelaneo\YJB_Logo.png')

st.set_page_config(page_title='Filtros', page_icon=logo_icono, layout='wide')
# st.image(logo2, width=100)
st.markdown('''
<h1 style="text-align:center;">Filtro de Tratamientos YJB</h1><br>
''', unsafe_allow_html=True)

st.markdown('<p style="text-align:center;">Esta API tiene como propósito poder filtrar valores acorde a Tratamientos y Especialidades para facilitar el servicio al cliente.</p><br>', unsafe_allow_html=True)

    #   Creación Tabla

df = pd.read_excel(r'C:\Users\Cesar\Downloads\aa.xlsx',sheet_name=1)
df.index = df['Especialidad']
df = df.drop('Especialidad', axis=1)
df = df.sort_index(ascending=True)
df['Precio Lista'] = df['Precio Lista'].apply('{:,}'.format)
df['Alianza'] = df['Alianza'].apply('{:,}'.format)
df['Familia'] = df['Familia'].astype(float)
df = df.fillna('0')
df['Familia'] = df['Familia'].astype(int)
df['Familia'] = df['Familia'].apply('{:,}'.format)
df = df.replace('0', '')

st.write('Lista de Descuentos Actuales:')
dctos = pd.DataFrame([['20 %', '40 %']], index=['Descuento [%]'], columns=['Convenio / Alianza', 'Familia'])
st._legacy_dataframe(dctos)

st.write('---')

    #   Filtros

sel_especialidad = st.selectbox('Busca por Especialidad:', options=df.index.unique(), index=3)

if sel_especialidad:
    df_filtrada = df[df.index==sel_especialidad].sort_values(by=['Servicios'])

# st._legacy_dataframe(data=df)
st._legacy_dataframe(data=df_filtrada)
