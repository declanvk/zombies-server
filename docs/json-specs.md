# From Server to Player

## Player Join Response (3)
Sent from server to player to notify successful room join.

```json
{
    "pkt_name": "player_join_response",
    "status": "success" | "failure",
    "aux_data": {
        "room_code": "room code (string)",
        "character": "character ident (number)",
        "is_god": "true" | "false",
    } | "failure reason (string)"
}
```

## Game Starting (6)
Sent from server to players

```json
{
    "pkt_name": "game_starting",
}
```

# Game Over (10)
Sent from server to players to notify game end

```json
{
    "pkt_name": "game_over",
    "winner": "normal" | "zombies" | "none",
}
```

# Change State (?)
Sent from server to players to notify them on changing from normal to zombie, or vice versa, or other important changes
```json
{
    "pkt_name": "status_change",
    "type": "zombie-change",
    "zombie-change": { "new-state": "zombie" | "normal" }
}
```

# To Server from Player

## Player Join Request (2)
Sent from player to server when user types in code/name.

```json
{
    "pkt_name": "player_join_request",
    "room_code": "room code (string)",
    "user_name": "user name (string)",
}
```

## Make Move (7)
Sent from player to server when a button state changes

```json
{
    "pkt_name": "make_move",
    "origin": "normal" | "god",
    "action": {
        "key": "up" | "down" | "left" | "right",
        "state": "pressed" | "released"
    } | {
        "code": "some identifying string for god moves"
    }
}
```

# From Server to Host

## Room Code (1)
Sent from server to host as soon as socket is opened

```json
{
    "pkt_name": "room_code",
    "room_code": "room code (string)"
}
```

## Player Joined (4)
Sent from server to host when a player joins. Packet includes ALL currently joined players.

```json
{
    "pkt_name": "player_joined",
    "players": [
        {"user_name": "user 1 name (string)", "character": "character name (string)"},
        {"user_name": "user 2 name (string)", "character": "character name (string)"}
    ],
    "new_player_name": "new player name (string)"
}
```

# To Server From Host

## Request Game Start (5)
Sent from host to server to start game

```json
{
    "pkt_name": "request_start_game"
}
```

# From Server To Viewer

## Game Starting (6)
Sent from server to viewers

```json
{
    "pkt_name": "game_starting",
}
```

# Game Over (10)
Sent from server to players to notify game end

```json
{
    "pkt_name": "game_over",
    "winner": "normal" | "zombies" | "none",
}

## Game Tick (8)
Sent from server to all viewers

```json
{
    "pkt_name": "game_tick",
    "player_pos_data": [{"player_id":
                            {
                                "position":{"x":0,"y":0},
                                "isZombie":false
                            }
                         },
                         true]
}
```

## Request Game View Response (?)
Sent from server to view in response to game view request

```json
{
    "pkt_name": "game_view_response",
    "view_status": "success" | "failure",
    "aux_data": "failure reason (string, conditional on failure)" | {
        "current_players": [
            {
                "player_id": "player id",
                "user_name": "user 1 name (string)",
                "character": "character name (string)"
            },
            {
                "player_id": "player id",
                "user_name": "user 2 name (string)",
                "character": "character name (string)"
            },
            // ...
        ],
        "board_description": {
            "width": "number",
            "height": "number",
            "player_radius": "number"
        }
    }
}
```

# To Server From Viewer

## Request Game View (?)

```json
{
    "pkt_name": "request_game_view",
    "room_code": "room code (string)"
}
```
