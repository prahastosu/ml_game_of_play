# Requirement

## Class Player

### Atribute
```java
public String obj_name; // player name
public String obj_name_in; // player name in game maps
public int obj_cur_hlt; // current health
public int obj_max_hlt; // max health
public int obj_cur_def; // current def
public int obj_max_def; // max def
public int obj_cur_man; // current mana
public int obj_max_man; // max mana
public int obj_n_atk; // normal attack
public String obj_n_eff; // normal effect
public int obj_n_rng; // normal range
public String obj_n_typ; // normal type (i - single, o - areal, c - slice, s - strike)
public int obj_s_atk; // skill attack
public String obj_s_eff; // skill effect
public int obj_s_rng; // skill range
public String obj_s_typ; // skill type (i - single, o - areal, c - slice, s - strike)
public int obj_b_atk; // burst attack
public String obj_b_eff; // burst effect
public int obj_b_rng; // burst range
public String obj_b_typ; // burst type (i - single, o - areal, c - slice, s - strike)
public String obj_eff = ""; // status effect element on player (b - burn, f - freeze, w - wet, e - electrocuted)
public String obj_eff_time = 0; // status effect time (max 5)
```
### Function

#### takeDamage
```java
public void takeDamage (int damage) {
  int damageTake = 0;
  if damage > obj_cur_def {
    damageTake = damage - obj_cur_def;
  }
  obj_cur_def -= int(0.5 * obj_cur_def);
  obj_cur_hlt -= damageTake;
}
```

#### updateEffect
```java
public void updateEffect(String effect) {
  if obj_eff == "" {
    obj_eff = effect;
    obj_eff_time = 5;
  } else if obj_eff == "b" {
    if effect == "e" {
      obj_eff = "";
      obj_eff_time = 0;
      obj_cur_hlt -= 10;
    } else if effect == "w" {
      obj_eff = "";
    } else if effect == "f" {
      obj_eff = "w";
      obj_eff_time = 5;
    } else if effect == "b" {
      obj_eff_time = 5;
    }
  } else if obj_eff == "f" {
    if effect == "e" {
      obj_eff = "";
      obj_eff_time = 0;
      obj_cur_hlt -= 5;
    } else if effect == "w" {
      obj_eff_time = 5;
      obj_cur_hlt -= 2;
    } else if effect == "f" {
      obj_eff_time = 5;
    } else if effect == "b" {
      obj_eff = "w";
      obj_eff_time = 5;
    }
  } else if obj_eff == "e" {
    if effect == "e" {
      obj_eff_time = 5;
    } else if effect == "w" {
      obj_eff_time = 5;
      obj_cur_hlt -= 2;
    } else if effect == "f" {
      obj_eff = "";
      obj_eff_time = 0;
      obj_cur_hlt -= 5;
    } else if effect == "b" {
      obj_eff = "";
      obj_eff_time = 0;
      obj_cur_hlt -= 10;
    }
  } else if obj_eff == "w" {
    if effect == "e" {
      obj_eff = "e"
      obj_eff_time = 5;
    } else if effect == "w" {
      obj_eff_time = 5;
    } else if effect == "f" {
      obj_eff = "f"
      obj_eff_time = 5;
    } else if effect == "b" {
      obj_eff = "";
    }
  }
}
```


## Class MapPoint

### Atribute
```
public int pos_x // position x
public int pos_y // position y
public Player player // player
```
