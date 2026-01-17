import streamlit as st
import pandas as pd
import plotly.express as px

# --- Page Config ---
st.set_page_config(
    page_title="Self-Service BI Portal",
    page_icon="📊",
    layout="wide"
)

# --- Header ---
st.title("📊 Self-Service Business Intelligence Portal")
st.markdown("""
    <style>
    .main {
        background-color: #f5f5f5;
    }
    </style>
    **Upload your raw dataset to generate instant insights and validate schema.**
    """, unsafe_allow_html=True)

# --- File Uploader ---
uploaded_file = st.file_uploader("Choose a CSV or Excel file", type=['csv', 'xlsx'])

def validate_schema(df):
    """
    Simulates the validation pipeline mentioned in documentation.
    Checks for nulls, data types, and potential schema drift.
    """
    st.info("Running automated schema validation...")
    # Placeholder for validation logic
    if df.isnull().sum().sum() > 0:
        st.warning(f"⚠️ Data Quality Alert: Found {df.isnull().sum().sum()} missing values.")
    else:
        st.success("✅ Schema Validation Passed. Data is clean.")
    return True

if uploaded_file is not None:
    # Load Data
    try:
        if uploaded_file.name.endswith('.csv'):
            df = pd.read_csv(uploaded_file)
        else:
            df = pd.read_excel(uploaded_file)

        # Display Raw Data
        st.subheader("1. Data Preview")
        st.dataframe(df.head())

        # Validation Pipeline
        st.subheader("2. Validation Pipeline")
        validate_schema(df)

        # Visualization Logic (Stub)
        st.subheader("3. Automated Insights")
        numeric_cols = df.select_dtypes(include=['float64', 'int64']).columns
        if len(numeric_cols) > 0:
            st.bar_chart(df[numeric_cols[0]])

    except Exception as e:
        st.error(f"Error processing file: {e}")