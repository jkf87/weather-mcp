# Weather MCP Server

한국 주요 도시의 날씨를 조회하는 MCP(Model Context Protocol) 서버입니다.

[Open-Meteo API](https://open-meteo.com/)를 사용하여 **무료**로 날씨 정보를 제공합니다. API 키가 필요 없습니다.

## 지원 도시

서울, 부산, 인천, 대구, 대전, 광주, 울산, 제주

## 설치 방법

### 소스에서 설치

```bash
git clone https://github.com/jkf87/weather-mcp.git
cd weather-mcp
pip install -e .
```

## MCP 클라이언트 설정

### Claude Code

```bash
claude mcp add weather-server -- weather-mcp
```

### Claude Desktop

`~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) 또는
`%APPDATA%\Claude\claude_desktop_config.json` (Windows)에 추가:

```json
{
  "mcpServers": {
    "weather-server": {
      "command": "weather-mcp"
    }
  }
}
```

### Gemini CLI

`~/.gemini/settings.json`에 추가:

```json
{
  "mcpServers": {
    "weather-server": {
      "command": "weather-mcp"
    }
  }
}
```

### Antigravity

`~/.antigravity/mcp.json`에 추가:

```json
{
  "mcpServers": {
    "weather-server": {
      "command": "weather-mcp"
    }
  }
}
```

### 기타 MCP 클라이언트

대부분의 MCP 클라이언트에서 다음과 같이 설정할 수 있습니다:

```json
{
  "mcpServers": {
    "weather-server": {
      "command": "weather-mcp"
    }
  }
}
```

## 제공 도구 (Tools)

### `get_weather`

특정 도시의 현재 날씨 정보를 조회합니다.

**매개변수:**
- `city` (string): 도시 이름 (기본값: "서울")

**예시 응답:**
```
서울 날씨 정보
━━━━━━━━━━━━━━━━━━━━
온도: 15.2°C
습도: 65%
풍속: 12.5 km/h
날씨: 맑음
━━━━━━━━━━━━━━━━━━━━
조회 시간: 2024-11-30 14:30:00
```

### `list_cities`

사용 가능한 도시 목록을 반환합니다.

## 사용 예시

AI 어시스턴트에게 다음과 같이 요청할 수 있습니다:

- "서울 날씨 알려줘"
- "부산이랑 제주 날씨 비교해줘"
- "오늘 대전 날씨 어때?"

## 직접 실행 (개발/테스트용)

```bash
# 서버 실행
weather-mcp

# 또는 Python 모듈로 실행
python -m weather_mcp.server
```

## 라이선스

MIT License
