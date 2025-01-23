# Discord Bot with Google Sheets Integration

This project is a Discord bot built using `discord.js` that integrates with Google Sheets for managing and tracking user data. It features command handling, logging, and the ability to update and retrieve data dynamically.

---

## Features

- **Google Sheets Integration**: Fetch, update, and manage data using Google Sheets API.
- **Custom Commands**:
  - `/artisan-update`: Add or update member data, including professions and levels.
  - `/artisan-search`: Search for member data or specific expertise levels.
  - `/artisan-logs`: View, download, or clear bot logs.
- **Dynamic Table Generation**: Generates table images using Puppeteer for visual data representation.
- **Role-Based Access Control**: Commands like `artisan-update` and `artisan-logs` are restricted to users with specific roles.
- **Error Logging and Rotation**: Uses `winston` for detailed error logging with daily log rotation.

---

## Prerequisites

Before you begin, ensure you have met the following requirements:

- Node.js and npm installed on your system.
- A Discord bot token. [Get one here](https://discord.com/developers/applications).
- Google Cloud credentials for accessing the Google Sheets API. [Learn more](https://console.cloud.google.com/).

---

## Installation

1. Clone the repository:

   git clone https://github.com/yourusername/your-repo.git
   cd your-repo

2. Install dependencies:

   npm install

## Environment Variables

Create a `.env` file in the root of the project and include the following environment variables:

```plaintext
DISCORD_TOKEN=your_discord_bot_token
CLIENT_ID=your_discord_client_id
GUILD_ID=your_discord_guild_id
SPREADSHEET_ID=your_google_sheets_id
CREDENTIALS_PATH=path_to_your_google_credentials.json
SHEET_NAME=your_google_sheet_name


## Spreadsheet Structure

The Google Sheets file used by this bot must have a specific structure to ensure proper functionality. Below are the details:

### Columns in the Spreadsheet

The spreadsheet should have the following columns in order (left to right):

| Column Name       | Description                                                   |
|-------------------|---------------------------------------------------------------|
| `Name`            | The name of the member.                                       |
| `Profession_1`    | The member's first profession.                                |
| `Level_1`         | The level of the first profession (e.g., Grandmaster, Master).|
| `Profession_2`    | The member's second profession.                               |
| `Level_2`         | The level of the second profession.                           |
| `Profession_3`    | The member's third profession.                                |
| `Level_3`         | The level of the third profession.                            |
| `Profession_4`    | The member's fourth profession.                               |
| `Level_4`         | The level of the fourth profession.                           |
| `Profession_5`    | The member's fifth profession.                                |
| `Level_5`         | The level of the fifth profession.                            |
| `Display_Name`    | The member's display name on Discord.                         |
| `Discord_ID`      | The Discord ID of the member.                                 |
| `Last_Update`     | A timestamp indicating the last time the row was updated.     |

### Example Spreadsheet Layout

| Name       | Profession_1 | Level_1  | Profession_2 | Level_2     | Profession_3 | Level_3     | Profession_4 | Level_4 | Profession_5 | Level_5 | Display_Name | Discord_ID       | Last_Update        |
|------------|--------------|----------|--------------|-------------|--------------|-------------|--------------|---------|--------------|---------|--------------|------------------|--------------------|
| Hammis     | Carpentry    | Master   | Tailoring    | Journeyman  | Alchemist    | Apprentice  |              |         |              |         | Hammis234    | 1234567890123456 | 2025-01-22 10:00:00|
| Jane Smith | Mining       | Master   |              |             |              |             |              |         |              |         | Jane#5678    | 2345678901234567 | 2025-01-22 10:30:00|

### Important Notes

1. **Column Order**: The order of columns is essential as the bot indexes them based on position.
2. **Empty Columns**: Columns such as `Profession_2`, `Level_2`, etc., can be left empty if not applicable for a member.
3. **Last_Update**: This column is automatically updated by the bot when a member's data is modified or added.
4. **Consistent Sheet Name**: The name of the sheet (tab) within the Google Sheets file must match the `SHEET_NAME` environment variable in the `.env` file.
5. **Permissions**: Ensure the bot's Google service account has the necessary permissions to access and modify the spreadsheet.



