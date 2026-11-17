# Amethyst Lump Claymore Mining Records Precautions / Notes

## 1. Preface
- These pathing routes were created assuming Inazuma and Enkanomiya puzzles are 100% solved and chests are 100% collected.
- When creating the script, **Noelle equipped with The Bell** was used as the active runner.
- Some pathing routes use Mavuika for transit.
- Team: Noelle, Mavuika, Escoffier, Barbara
- Estimated Time: 1 hour 35 minutes ~ 1 hour 40 minutes / 235 ~ 275 items

## 2. Configuration Overview
- Survivability slot skill: Barbara
- CD: `300`

- Combat script:

    ```text
    Noelle e
    Columbina attack(0.01),keypress(q),attack(0.2),e,wait(0.2),attack(0.4),keypress(e),charge(0.2),keypress(q),charge(0.12),attack(0.08),keypress(e),keypress(q),w(0.01),attack(0.2),keypress(e),keypress(q)
    Linnea attack(0.18),keypress(q),wait(0.1), ready,attack(0.05), e,attack(0.65), keypress(q),wait(0.1) ,keypress(q),attack(0.1)
    Mavuika attack(0.01),e
    Escoffier e,wait(0.26),attack(0.15),wait(0.26),keypress(q),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.2),keypress(q),attack(0.01)
    Barbara attack(0.2),wait(0.3),keypress(e), wait(0.2),keypress(e), click(middle), keypress(q),wait(0.2), keypress(q),keypress(e),wait(0.2), keypress(q) ,attack(0.6),charge(0.6),keypress(e),wait(0.3)
    Mavuika check,q
    Rosaria e,attack(0.4),keypress(q),attack(0.4),keypress(q),e
    Dehya e, attack(0.3), keypress(e), wait(0.3), wait(0.3)
    Noelle e,check,q,ready,charge(2.3)
    Kaedehara Kazuha attack(0.01),wait(0.25),e(hold),click(middle),wait(0.48),attack,wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.1),keydown(E),wait(0.55),keyup(E),click(middle),wait(0.45),attack,w(0.01),wait(0.19)
    ```

- Enable Faster Combat Finish Check
- Auto Pick Drops: Disabled
- Combat timeout: `45` seconds
- **Please adjust the combat script and combat timeout according to your own team lineup, character investment level, and preferences.**

## 3. Expected Yields

- **Narukami Island**: 42
  - Narukami Island (No Combat) = 27
  - Narukami Island (With Combat) = 15
- **Kannazuka**: 35
  - Kannazuka (No Combat) = 29
  - Kannazuka (With Combat) = 6
- **Yashiori Island**: 27
  - Yashiori Island (No Combat) = 23
  - Yashiori Island (With Combat) = 4
- **Watatsumi Island**: 24
  - Watatsumi Island (No Combat) = 20
  - Watatsumi Island (With Combat) = 4
- **Seirai Island**: 35
  - Seirai Island (No Combat) = 27
  - Seirai Island (With Combat) = 8
- **Tsurumi Island**: 26
  - Tsurumi Island (No Combat) = 24
  - Tsurumi Island (With Combat) = 2
- **Enkanomiya**: 46
  - Enkanomiya (No Combat) = 20
  - Enkanomiya (With Combat) = 26

**Expected Total: 235 items**

**Excluding Combat routes (-67) = 168 items**
