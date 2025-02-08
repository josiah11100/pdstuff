
const axios = require('axios');
const app = express();
const port = process.env.PORT || 3000;

app.get('/gamepasses/:userId', async (req, res) => {
    try {
        const userId = req.params.userId;
        const url = `https://www.roblox.com/users/inventory/list-json?assetTypeId=34&cursor=&itemsPerPage=100&pageNumber=1&userId=${userId}`;
        const response = await axios.get(url);
        res.json(response.data);
    } catch (error) {
        res.status(500).send('Error fetching data');
    }
});

app.listen(port, () => {
    console.log(`Proxy server running on port ${port}`);
});
