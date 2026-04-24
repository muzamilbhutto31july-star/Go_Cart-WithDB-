# Go_Cart-WithDB-

🧭 Receiver Setup Guide — How to Run the Project

🔹 1. Install the Required Software

Step 1 — Install Visual Studio
Go to: https://visualstudio.microsoft.com/downloads/
Download Visual Studio Community (Free).
During installation, select these workloads:

✅ .NET desktop development
After installation, open Visual Studio once to complete setup.

Step 2 — Install SQL Server
You’ll need two tools:
SQL Server Express (Database Engine)
SQL Server Management Studio (SSMS)
👉 Download both from Microsoft:
SQL Server Express: https://www.microsoft.com/en-us/sql-server/sql-server-downloads
SQL Server Management Studio (SSMS): https://aka.ms/ssmsfullsetup

Installation Tips:
When SQL Server installer asks for instance name → use default (SQLEXPRESS)
Authentication mode → choose Windows Authentication
🔹 2. Extract and Open the Project
Download the ZIP file sent by your friend (e.g. GoCartApplication.zip).
Right-click → Extract All...
Place it somewhere simple, e.g. C:\Projects\GoCartApplication\
Inside, open the file:
GoCartApplication.sln
This will open the project in Visual Studio.

🔹 3. Restore / Recreate the Database
Open SQL Server Management Studio (SSMS).
Connect to your server → expand “Databases”.
Right-click Databases → choose Restore Database...
Select Device → Add → browse for GoCart.bak
Click OK → Restore.
✅ You’ll now have a database named GoCart.



🔹 4. Update the Database Connection in Code
Now tell the project to connect to your local SQL Server.
In Visual Studio, open file:
DBConnection.cs
Locate the line similar to:

private SqlConnection conn = new SqlConnection(@"Data Source=DESKTOP-KPVESE3\SQLEXPRESS;Initial Catalog=GoCart;Integrated Security=True");


Replace the part before \SQLEXPRESS with your computer name.

To find it:

Press Windows + R → type cmd → Enter

Type:

hostname


Copy the result (e.g., DESKTOP-123ABC)

Update your code:

@"Data Source=DESKTOP-123ABC\SQLEXPRESS;Initial Catalog=GoCart;Integrated Security=True"


Save and rebuild the solution (Ctrl + Shift + B).


🔹 5. Run the Project

In Visual Studio → Click Start ▶️

The Login Form should appear.

Use the sample admin credentials you were provided (or insert new admin using SSMS if necessary).

✅ If everything is set up properly:

Login works

Dashboard opens

You can Add / Update / Delete categories and products

🔹 6. Common Troubleshooting

Problem	Solution

❌ “Connection property not initialized”	Database connection string incorrect — recheck your SQL Server name

❌ “Login failed for user”	Run Visual Studio as Administrator or use correct SQL authentication

❌ Missing tables or data	Re-run or restore the database .bak / .sql file

❌ Index out of range (DataGridView)	Click directly on rows (not blank space) before updating/deleting
