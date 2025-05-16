# Ideas
1. 230VAC -(AD-DC converter 5v output)-> Noisy 5V DC -(Filtering)-> Smooth 5VDC -(LM2662 switching regulator)-> 15VDC -(LM2662 switching regulator)-> ±15VDC
2. 230VAC -(AD-DC converter 5v output)-> Noisy 15VDC -(Filtering)-> Smooth 15VDC -(LM2662 switching regulator)-> ±15VDC

## AC-DC regulator 5V output modules:
- Hi-Link HLK-5M05
- Mean Well IRM-05-5
- Jameco PM05 series

## AC-DC regulator 15V output modules:
- Hi-Link HLK-10M15
- Mean Well IRM-15-15

## Filtering Circuits:
- pi filter (CLC)
- LC filter
- Ferrite Bead
- LDO

### Pi filter:
- very effective
- might cause ringing if not careful with inductor value

### LC filter:
- compact
- good for digital
- needs good ground to avoid reintroducing noise
- not as effective as pi for high freq noise

### Ferrite bead + Decoupling cap
- very compact
- very cheap
- not that effective for low frequency noise
- low current ratinng

### LDO
- most effective
- excess power is converted to heat
- needs heatsink

## Design Possibilty for filtering:
Noisy DC -(pi)->-(LDO)->-(ferrite bead)->-(decoupling cap)-> Smooth DC

Pi filter: kills high freq noise

LDO: kills low freq noise

Ferrite: kills any remaining noise, prevents noise injection from opamp ckt
