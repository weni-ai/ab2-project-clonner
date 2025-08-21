# Weni Project Cloner

A Jupyter notebook script that copies complete project configurations between Weni AI projects using the Weni API.

## What it copies

- **Agent customization**: name, role, personality, goal, and instructions
- **Knowledge bases**: text bases, link bases, and file bases
- **Smart updates**: Updates existing content instead of creating duplicates

## Prerequisites

- Python 3.7+
- Jupyter Notebook
- Weni API Bearer Token
- Source and destination project UUIDs

## Setup

1. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Create `.env` file** with your credentials:
   ```env
   BEARER_TOKEN=your_weni_bearer_token_here
   SOURCE_PROJECT_UUID=uuid_of_project_to_copy_from
   DESTINATION_PROJECT_UUID=uuid_of_project_to_copy_to
   ```

## Usage

1. **Start Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

2. **Open `main.ipynb`**

3. **Run the cells in order**:
   - **Setup** (Cell 1): Loads configuration
   - **Individual copies**: Run cells 9, 11, 13, 15 for specific components
   - **Complete copy**: Run cell 17 to copy everything at once
   - **Verification**: Run cell 19 to verify the copy

## Key Features

- **Safe copying**: Instructions are copied without IDs to avoid conflicts
- **Smart text base handling**: Updates existing text bases instead of duplicating
- **Content base UUID resolution**: Automatically resolves project UUIDs to content base UUIDs
- **Error handling**: Comprehensive error reporting for each step

## Important Notes

- The destination project will be **overwritten** with source project data
- Instructions are copied as new entries (IDs are stripped)
- Text bases are updated if they exist, created if they don't
- File downloads and uploads may take time depending on file sizes

## Example Output

```
✅ Successfully copied agent customization to destination project
✅ Updated text base 1/1: Canais de atendimento...
✅ Successfully copied 6/6 link bases
✅ Successfully copied 0/0 file bases
```

---

**⚠️ Warning**: Always test with non-production projects first. This script modifies the destination project's configuration.
