# Plots
## Settings and Setup
The runs were done with the following settings, based on the options of the rust/gdscript benchmark applications:

all:
- `initial wave size: 0`
- `mob spawn intervall`
- `bot player: true`
- `safe mode: true`

| # | mob spawns per second | add calculations | calculate n times per mob per frame |
| --: | -----: | ----- | -----: |
| 1 | 10 | false | - |
| 2 | 10 | true | 1 |
| 3 | 5 | true | 10 |
| 4 | 3 | true | 50 |
| 4b | 3 | true | 50 |
| 5 | 2 | true | 100 |
| 6 | 1 | true | 200 |

Hardware:
- MacBook Pro Retina 13 Inch early 2015
- 2.7 GHz Dual Core Intel Core i5
- 8 GB 1867 MHz DDR3
- 128 GB flash drive

OS:
- macOS 12.4 Monterey

## Series 1
### GDScript 
![gds](data/eval_run_1/gds_mean.png)

### Rust
![rust](data/eval_run_1/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_1/diff_rust-gds_mean.png)

## Series 2
### GDScript 
![gds](data/eval_run_2/gds_mean.png)

### Rust
![rust](data/eval_run_2/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_2/diff_rust-gds_mean.png)

## Series 3
### GDScript 
![gds](data/eval_run_3/gds_mean.png)

### Rust
![rust](data/eval_run_3/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_3/diff_rust-gds_mean.png)

## Series 4
### GDScript 
![gds](data/eval_run_4/gds_mean.png)

### Rust
![rust](data/eval_run_4/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_4/diff_rust-gds_mean.png)

## Series 4b
### GDScript 
![gds](data/eval_run_4b/gds_mean.png)

### Rust
![rust](data/eval_run_4b/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_4b/diff_rust-gds_mean.png)

## Series 5
### GDScript 
![gds](data/eval_run_5/gds_mean.png)

### Rust
![rust](data/eval_run_5/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_5/diff_rust-gds_mean.png)

## Series 6
### GDScript 
![gds](data/eval_run_6/gds_mean.png)

### Rust
![rust](data/eval_run_6/rust_mean.png)

### Difference Rust-GDScript
![rust](data/eval_run_6/diff_rust-gds_mean.png)
