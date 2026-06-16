require("dotenv").config();

const express = require("express");
const multer = require("multer");
const mysql = require("mysql2/promise");
const { BlobServiceClient } = require("@azure/storage-blob");

const app = express();
const upload = multer({ storage: multer.memoryStorage() });

app.set("view engine", "ejs");
app.use(express.urlencoded({ extended: true }));

const dbConfig = {
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  port: 3306,
  ssl: {
    rejectUnauthorized: false
  }
};

app.get("/", (req, res) => {
  res.redirect("/submit-task");
});

app.get("/submit-task", (req, res) => {
  res.render("index", { message: null, error: null });
});

app.post("/submit-task", upload.single("file"), async (req, res) => {
  const { nim, name, kelas, course } = req.body;

  if (!req.file) {
    return res.render("index", {
      message: null,
      error: "File tugas wajib diupload."
    });
  }

  try {
    const blobServiceClient = BlobServiceClient.fromConnectionString(
      process.env.AZURE_STORAGE_CONNECTION_STRING
    );

    const containerClient = blobServiceClient.getContainerClient(
      process.env.CONTAINER_NAME
    );

    const fileName = `${nim}_${Date.now()}_${req.file.originalname}`;
    const blockBlobClient = containerClient.getBlockBlobClient(fileName);

    await blockBlobClient.uploadData(req.file.buffer, {
      blobHTTPHeaders: {
        blobContentType: req.file.mimetype
      }
    });

    const fileUrl = blockBlobClient.url;

    const connection = await mysql.createConnection(dbConfig);

    await connection.execute(
      `INSERT INTO submissions 
      (nim, name, class, course, file_url, status, submitted_at)
      VALUES (?, ?, ?, ?, ?, ?, NOW())`,
      [nim, name, kelas, course, fileUrl, "Submitted"]
    );

    await connection.end();

    res.render("index", {
      message: "Tugas berhasil dikumpulkan.",
      error: null
    });
  } catch (error) {
    console.error(error);

    res.render("index", {
      message: null,
      error: "Terjadi kesalahan: " + error.message
    });
  }
});

app.get("/task-list", async (req, res) => {
  try {
    const connection = await mysql.createConnection(dbConfig);

    const [rows] = await connection.execute(
      "SELECT * FROM submissions ORDER BY submitted_at DESC"
    );

    await connection.end();

    res.render("task-list", { rows });
  } catch (error) {
    res.send("Error: " + error.message);
  }
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Server berjalan di port ${PORT}`);
});