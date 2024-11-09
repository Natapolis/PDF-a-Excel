import PyPDF2
import pandas as pd
import tabula
import tkinter as tk
from tkinter import filedialog, messagebox
from pathlib import Path

class PDFToExcelConverter:
    def __init__(self):
        self.root = tk.Tk()
        self.root.title("PDF to Excel Converter")
        self.root.geometry("400x200")
        self.setup_ui()

    def setup_ui(self):
        # Create and pack widgets
        title_label = tk.Label(self.root, text="PDF to Excel Converter", font=("Arial", 14, "bold"))
        title_label.pack(pady=10)

        select_button = tk.Button(self.root, text="Select PDF File", command=self.convert_pdf)
        select_button.pack(pady=20)

        self.status_label = tk.Label(self.root, text="")
        self.status_label.pack(pady=10)

    def convert_pdf(self):
        # Open file dialog
        pdf_file = filedialog.askopenfilename(
            title="Select PDF File",
            filetypes=[("PDF files", "*.pdf")]
        )
        
        if not pdf_file:
            return

        try:
            # Update status
            self.status_label.config(text="Converting... Please wait")
            self.root.update()

            # Read tables from PDF
            tables = tabula.read_pdf(pdf_file, pages='all')
            
            # Create output filename
            output_file = Path(pdf_file).with_suffix('.xlsx')
            
            # Create Excel writer object
            with pd.ExcelWriter(output_file) as writer:
                # Write each table to a different worksheet
                for i, table in enumerate(tables):
                    table.to_excel(writer, sheet_name=f'Sheet{i+1}', index=False)

            self.status_label.config(text="Conversion completed successfully!")
            messagebox.showinfo("Success", f"File saved as: {output_file}")

        except Exception as e:
            self.status_label.config(text="Error during conversion")
            messagebox.showerror("Error", f"An error occurred: {str(e)}")

    def run(self):
        self.root.mainloop()

if __name__ == "__main__":
    app = PDFToExcelConverter()
    app.run()
