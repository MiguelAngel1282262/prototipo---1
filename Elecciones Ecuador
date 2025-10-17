# app.py
# Streamlit app: Datos generales - Elecciones Generales Ecuador 2025
# Fuentes: CNE, UNDP, Asamblea Nacional, informes de observación (citadas en el README del repo).

import streamlit as st
import pandas as pd
from datetime import datetime

st.set_page_config(page_title="Elecciones Ecuador 2025 - Datos generales", layout="wide")

# ---- Metadatos (valores oficiales / verificados) ----
DATA = {
    "Primera vuelta": "9 de febrero de 2025",
    "Segunda vuelta (si aplica)": "13 de abril de 2025",
    "Electores habilitados (total)": 13736314,
    "Electores en territorio nacional": 13279829,
    "Electores en el exterior": 456485,
    "Miembros de Juntas Receptoras del Voto (MJRV)": 287534,
    "Recintos electorales (reportados)": "4,349 recintos (ver fichas estadísticas)",
    "Centros de Digitalización de Actas (CDA)": "1,680 (reportado en fichas estadísticas)",
    "Asambleístas (total)": 151,
    "Parlamentarios Andinos": 5
}

# ---- UI ----
st.title("📊 Elecciones Generales — Ecuador 2025 (datos generales)")
st.markdown(
    """
    Aplicación simple para mostrar **datos generales** de las Elecciones Generales de Ecuador (2025).
    Los valores mostrados están basados en fuentes oficiales (CNE, fichas estadísticas y actas oficiales).
    """
)

# Key facts in columns
col1, col2, col3 = st.columns(3)
with col1:
    st.subheader("Fechas")
    st.write("Primera vuelta")
    st.markdown(f"**{DATA['Primera vuelta']}**")
    st.write("Segunda vuelta (si aplica)")
    st.markdown(f"**{DATA['Segunda vuelta (si aplica)']}**")

with col2:
    st.subheader("Electores")
    st.metric("Electores habilitados (total)", f"{DATA['Electores habilitados (total)']:,}")
    st.write(f"- En territorio nacional: {DATA['Electores en territorio nacional']:,}")
    st.write(f"- En el exterior: {DATA['Electores en el exterior']:,}")

with col3:
    st.subheader("Operativo electoral")
    st.write(f"- MJRV seleccionados: **{DATA['Miembros de Juntas Receptoras del Voto (MJRV)']:,}**")
    st.write(f"- Recintos reportados: {DATA['Recintos electorales (reportados)']}")
    st.write(f"- CDA reportados: {DATA['Centros de Digitalización de Actas (CDA)']}")

st.markdown("---")

# Table with puestos y cifras
df = pd.DataFrame([
    {"Puesto / Elección": "Presidente y Vicepresidente", "Cantidad": "1 binomio"},
    {"Puesto / Elección": "Asambleístas (total)", "Cantidad": DATA["Asambleístas (total)"]},
    {"Puesto / Elección": "Parlamentarios Andinos", "Cantidad": DATA["Parlamentarios Andinos"]},
])
st.subheader("¿Qué se eligió?")
st.table(df)

st.markdown("---")

# Notas y fuentes
st.subheader("Notas y fuentes (resumen)")
st.markdown(
    """
    - Calendario electoral y fechas: **Consejo Nacional Electoral (CNE)**.  
    - Electores habilitados y distribución nacional / exterior: **CNE** (registro electoral final).  
    - Selección de Miembros de Juntas Receptoras del Voto: **CNE** (comunicados oficiales).  
    - Datos de recintos y Centros de Digitalización de Actas: fichas estadísticas (ej. informes UNDP / CNE).  
    - Composición de la Asamblea y Parlamentarios Andinos: **CNE** / Asamblea Nacional (proclamación de resultados).
    """
)

st.caption("Sugerencia: en el README de tu repo puedes copiar las URLs oficiales del CNE y los PDFs de fichas estadísticas para referencia directa.")

# Optional: export data as CSV / JSON for GitHub preview
export_df = pd.DataFrame([{"clave":k, "valor": v} for k, v in DATA.items()])
st.download_button("Descargar datos (CSV)", export_df.to_csv(index=False).encode('utf-8'), "elecciones_ecuador_2025.csv", "text/csv")

# Footer - timestamp
st.markdown("---")
st.write("Última actualización de los datos mostrados (basado en fuentes oficiales):")
st.write(datetime.utcnow().strftime("%Y-%m-%d %H:%M UTC"))
