Issues and solutions

- Time manipulation:
    user changes the device time then replays old valid conditions as if they are current.
  solution:
    reject requests with old timestamps and enforce short validity windows

- Weather API exploitation:
    Attackers exploit delay in updates and wrong region mapping
  solution:
    use multiple weather APIs, apply confidence scoring on weather data

- Multi account attacks:
    1 persson creates multiple accounts and each account claims payout
  solution:
    strong KYC verification, limit accounts per device or ip    