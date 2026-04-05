# NexaForgeX - Facebook Poster

Automatically post content to Facebook from a CSV spreadsheet.

## Features

✨ Post messages to Facebook pages
📸 Post with images
⏱️ Built-in rate limiting to respect API limits
📊 Batch processing from CSV files
🔒 Secure credential management with environment variables

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- Facebook Page Access Token
- Facebook Page ID

## Installation

1. Clone the repository:
```bash
git clone https://github.com/asif0993/nexaforgex.git
cd nexaforgex
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file from template:
```bash
cp .env.example .env
```

4. Add your Facebook credentials to `.env`:
```
FACEBOOK_ACCESS_TOKEN=your_page_access_token_here
FACEBOOK_PAGE_ID=your_page_id_here
```

## Getting Facebook Credentials

### Step 1: Create a Facebook App
1. Go to [Facebook Developers](https://developers.facebook.com/)
2. Create a new app (Business type)
3. Add "Facebook Login" product

### Step 2: Get Page Access Token
1. Go to your app's Settings → Basic
2. Add Facebook Pages product
3. Navigate to Messenger → Settings
4. Generate a Page Access Token for your page
5. Copy the token to `.env`

### Step 3: Get Page ID
1. Visit your Facebook page
2. Check the URL or use [Graph API Explorer](https://developers.facebook.com/tools/explorer/)
3. Copy your Page ID to `.env`

## Usage

### Prepare Your CSV File

Create a `posts.csv` file:

```csv
message,image_url
"Check out our latest product!",https://example.com/image1.jpg
"New blog post live",https://example.com/image2.jpg
"Special offer this week",
```

### Run the Script

#### Basic usage (messages only):
```bash
npm start
```

#### With custom CSV file:
```bash
node facebook-poster.js myfile.csv message
```

#### With images:
```bash
npm run post-with-images
node facebook-poster.js posts.csv message image_url
```

## CSV Format

Your spreadsheet should have these columns:

| Column | Required | Description |
|--------|----------|-------------|
| message | ✅ Yes | The post content |
| image_url | ❌ No | URL to image (if posting images) |

## API Response

Successful posts return:
```json
{
  "id": "123456_789012"
}
```

## Error Handling

The script handles common errors:
- Missing environment variables
- Invalid CSV format
- Facebook API rate limiting (1 second delay between posts)
- Network errors

## Rate Limiting

Facebook has rate limits. The script adds a 1-second delay between posts to stay compliant.

## Examples

### Example 1: Simple Text Posts
```csv
message
"Hello Facebook!"
"Check out our website"
"New update available"
```

### Example 2: Posts with Images
```csv
message,image_url
"New product launch",https://example.com/product.jpg
"Customer spotlight",https://example.com/customer.jpg
```

## Troubleshooting

**Error: FACEBOOK_ACCESS_TOKEN not set**
- Make sure `.env` file exists and has valid credentials

**Error: Invalid access token**
- Check token expiration at Facebook Developer Dashboard
- Generate a new token if needed

**Posts not appearing**
- Check page permissions
- Verify access token has `pages_manage_posts` permission

## License

MIT

## Support

For issues or questions, open an issue on GitHub.