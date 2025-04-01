<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Divider Styles Test</title>
    <style>
        body {
            background-color: rgb(247, 247, 247);
            font-family: "Open Sans", sans-serif;
            padding: 20px;
        }
        .section {
            padding: 20px;
            background: white;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        .divider-thin {
            border: none;
            border-top: 1px solid #ddd;
            margin: 20px 0;
        }
        .divider-gradient {
            border: none;
            height: 1px;
            background: linear-gradient(to right, transparent, #ccc, transparent);
            margin: 20px 0;
        }
        .divider-dashed {
            border: none;
            border-top: 1px dashed #ccc;
            margin: 20px 0;
        }
        .divider-space {
            height: 20px;
        }
    </style>
</head>
<body>
    <div class="section">Section 1</div>
    <hr class="divider-thin">
    <div class="section">Section 2</div>
    <hr class="divider-gradient">
    <div class="section">Section 3</div>
    <hr class="divider-dashed">
    <div class="section">Section 4</div>
    <div class="divider-space"></div>
    <div class="section">Section 5 (Spacer instead of a line)</div>
</body>
</html>
