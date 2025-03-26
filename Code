import streamlit as st
import requests

st.title("English to SQL Translator")

# Input for the natural language query
query = st.text_input("Enter your query (e.g., Show all employees in IT)")

if st.button("Translate & Fetch"):
    if query:
        response = requests.post("http://localhost:5000/translate", json={"query": query})
        if response.status_code == 200:
            data = response.json()
            st.subheader("SQL Query:")
            st.code(data.get("query", "Error generating SQL"), language="sql")
            
            st.subheader("Results:")
            st.json(data.get("results", {}))
        else:
            st.error("Error fetching SQL translation.")
    else:
        st.warning("Please enter a query.")
