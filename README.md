# 🐋 WhalePulse AI

Real-time BSC (Binance Smart Chain) whale detection Telegram bot with AI-powered analysis.

## Features

- 🐋 **Real-time Whale Detection** - Monitors BSC for large transactions
- 🦄 **PancakeSwap Integration** - Tracks swaps on PancakeSwap V2 & V3
- 🤖 **AI Analysis** - Optional Groq-powered analysis of whale movements
- 🚨 **Instant Alerts** - Telegram notifications with rich formatting
- ⚡ **Anti-Spam** - Rate limiting and cooldown mechanisms
- 📊 **Statistics** - Track bot performance and whale activity

## Tech Stack

- **Node.js** (Latest LTS)
- **ethers.js** - Blockchain interaction
- **node-telegram-bot-api** - Telegram bot integration
- **WebSocket RPC** - Real-time BSC connection

## Telegram Commands

- `/start` - Start the bot and see welcome message
- `/status` - View bot statistics
- `/help` - Show help message

## Alert Format

```
🚨 Whale Activity Detected

💰 Token: $TOKEN
📊 Value: 100.00 BNB
👛 Wallet: 0x1234...5678
🟢 Action: BUY
🦄 DEX: PancakeSwap V2

🔗 View Transaction

━━━━━━━━━━━━━━━
🤖 AI Analysis

📈 Signal: ACCUMULATION
🎯 Confidence: HIGH
⚖️ Bias: BULLISH

💡 Large accumulation detected, likely institutional interest.

━━━━━━━━━━━━━━━
🐋 WhalePulse AI - Real-time Whale Detection
```

## Whale Detection Rules

Alerts are triggered when:

1. **BNB Transfer** ≥ `MIN_WHALE_THRESHOLD` (default: 30 BNB)
2. **Token Swap** value ≥ `MIN_TOKEN_SWAP_VALUE` (default: $10,000)
3. **PancakeSwap Interaction** with significant volume

## Anti-Spam Logic

- **Cooldown**: Same wallet won't trigger alerts within `ALERT_COOLDOWN_MS` (default: 10s)
- **Rate Limiting**: Max 6 alerts per minute
- **Duplicate Prevention**: Tracks recent alerts to avoid duplicates

## Configuration Options

| Variable | Description | Default |
|----------|-------------|---------|
| `TELEGRAM_BOT_TOKEN` | Telegram bot token | Required |
| `TELEGRAM_CHAT_ID` | Channel/chat ID | Required |
| `BSC_RPC_WSS` | BSC WebSocket RPC | Required |
| `GROQ_API_KEY` | Groq API for AI | Optional |
| `MIN_WHALE_THRESHOLD` | Min BNB for alert | 30 |
| `MIN_TOKEN_SWAP_VALUE` | Min token swap value | 10000 |
| `ALERT_COOLDOWN_MS` | Alert cooldown per wallet | 10000 |

## Troubleshooting

### Bot not sending messages

1. Check bot is admin in the channel/group
2. Verify `TELEGRAM_CHAT_ID` is correct
3. Check bot token is valid
4. Ensure no Telegram API restrictions

### No whale alerts

1. Check `MIN_WHALE_THRESHOLD` is not too high
2. Verify BSC WebSocket connection in logs
3. Monitor blockchain activity on BscScan
4. Try lowering thresholds for testing

### AI analysis not appearing

1. Verify `GROQ_API_KEY` is set
2. AI only triggers for high-value transactions (2x threshold)
3. Check API quota at Groq Console
4. Logs will show if AI analysis fails

### Connection issues

1. Try alternative BSC RPC endpoints:
   - `wss://bsc.drpc.org`
   - `wss://bsc-dataseed.binance.org/`
   - `wss://bsc.nodereal.io/ws/v1/YOUR_API_KEY`
2. Check firewall/proxy settings
3. Ensure stable internet connection

## Monitoring

Check logs for real-time information:

```bash
# Follow logs (if running in background)
tail -f bot.log

# Or use journalctl if using systemd
journalctl -u whalepulse -f
```

## Performance

- **Block Processing**: ~3 seconds per block
- **Memory Usage**: ~100-200MB
- **CPU Usage**: Minimal (5-10%)
- **Network**: WebSocket (persistent connection)

## Security Best Practices

1. Never commit `.env` file to version control
2. Use strong, unique bot tokens
3. Rotate API keys regularly
4. Monitor bot logs for suspicious activity
5. Limit bot permissions in Telegram

## License

MIT

## Support

For issues and questions:
- Check the troubleshooting section
- Review logs for error messages
- Verify all environment variables are set correctly

---

**🐋 WhalePulse AI - Stay Ahead of the Whales!**
