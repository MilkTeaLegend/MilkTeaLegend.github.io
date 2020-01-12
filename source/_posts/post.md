---
layout: my
title: 二维能带的处理方法(Quantum Espresso)
date: 2020-01-12 03:18:07
tags: 凝聚态计算
---

# 二维能带的处理方法
## self-consistent field calculation and none self-consistent calculation is prepared

```
&control
    calculation = 'scf',
    verbosity = 'low'
    prefix = 'PTEB'
    outdir = './tmp/'
    pseudo_dir = '/mnt/e/calculatechemistry/FirstPrinciple/BURAI1.3.2_Windows/pseudopot/'
 /
 &system
    a           =  1.64969e+01
    b           =  1.64809e+01
    c           =  5.00000e+01
    cosab       = -5.00000e-01
    degauss     =  1.00000e-02
    ecutrho     =  150
    ecutwfc     =  25
    ibrav       = 12
    nat         = 30
    ntyp        = 2
    occupations = 'smearing',
    smearing = 'gauss',
    degauss = 0.01
 /
 &electrons
    mixing_beta = 0.7
 /
 &IONS
	ion_dynamics = 'bfgs'
/

ATOMIC_SPECIES
C      12.01070  C.pbe-rrkjus.UPF
H       1.00794  H.pbe-rrkjus.UPF

ATOMIC_POSITIONS {angstrom}
C       3.759785   7.611155  14.310000
C       3.760673   9.047720  14.311500
C       2.543351   9.754656  14.318500
C       2.540098  11.162104  14.319500
C       4.977963   9.754085  14.308000
C       4.981391  11.161391  14.309500
C       1.295809  11.880316  14.324000
C       3.760766  11.862617  14.315500
C       6.225577  11.879459  14.306000
C      -6.953221  13.788314  14.301000
C      -4.488410  13.804585  14.308000
C       2.531580   0.233219  14.300500
C       2.534926   1.640667  14.296500
C      -2.023371  13.787029  14.320000
C       4.972708   0.232220  14.309500
C       4.969455   1.639668  14.307000
C       3.752380   2.346747  14.301000
C       3.753598   3.783312  14.299500
C       0.234245  12.489482  14.323000
C       3.757615   6.387113  14.301500
C       8.482504  13.178148  14.300000
C       3.755934   5.007354  14.298500
C      -0.961807  13.177863  14.321500
C       7.286753  12.489625  14.300000
H       1.602888   9.212001  14.325000
H       5.918147   9.210859  14.304000
H       3.761210  12.948498  14.315500
H      -4.488936  12.718847  14.312000
H       1.594577   2.183608  14.290000
H       5.909835   2.182466  14.310500

K_POINTS {automatic}
2 2 2 0 0 0
```

## none self-consistent field calculation


```
 &control
    calculation = 'nscf',
    verbosity = 'low'
    prefix = 'PTEB'
    outdir = './tmp/'
    pseudo_dir = '/mnt/e/calculatechemistry/FirstPrinciple/BURAI1.3.2_Windows/pseudopot/'
 /
 &system
    a           =  1.64969e+01
    b           =  1.64809e+01
    c           =  5.00000e+01
    cosab       = -5.00000e-01
    degauss     =  1.00000e-02
    ecutrho     =  150
    ecutwfc     =  25
    ibrav       = 12
    nat         = 30
    ntyp        = 2
    occupations = 'smearing',
    smearing = 'gauss',
    degauss = 0.01
 /
 &electrons
    mixing_beta = 0.7
 /
 &IONS
	ion_dynamics = 'bfgs'
/

ATOMIC_SPECIES
C      12.01070  C.pbe-rrkjus.UPF
H       1.00794  H.pbe-rrkjus.UPF

ATOMIC_POSITIONS {angstrom}
C       3.759785   7.611155  14.310000
C       3.760673   9.047720  14.311500
C       2.543351   9.754656  14.318500
C       2.540098  11.162104  14.319500
C       4.977963   9.754085  14.308000
C       4.981391  11.161391  14.309500
C       1.295809  11.880316  14.324000
C       3.760766  11.862617  14.315500
C       6.225577  11.879459  14.306000
C      -6.953221  13.788314  14.301000
C      -4.488410  13.804585  14.308000
C       2.531580   0.233219  14.300500
C       2.534926   1.640667  14.296500
C      -2.023371  13.787029  14.320000
C       4.972708   0.232220  14.309500
C       4.969455   1.639668  14.307000
C       3.752380   2.346747  14.301000
C       3.753598   3.783312  14.299500
C       0.234245  12.489482  14.323000
C       3.757615   6.387113  14.301500
C       8.482504  13.178148  14.300000
C       3.755934   5.007354  14.298500
C      -0.961807  13.177863  14.321500
C       7.286753  12.489625  14.300000
H       1.602888   9.212001  14.325000
H       5.918147   9.210859  14.304000
H       3.761210  12.948498  14.315500
H      -4.488936  12.718847  14.312000
H       1.594577   2.183608  14.290000
H       5.909835   2.182466  14.310500

K_POINTS {automatic}
3 3 1 0 0 0
```

## band calculation

### Similar to ordinary band calculation, but requires more sampling points.

```
 &control
    calculation = 'bands',
    verbosity = 'low'
    prefix = 'PTEB'
    outdir = './tmp/'
    pseudo_dir = '/mnt/e/calculatechemistry/FirstPrinciple/BURAI1.3.2_Windows/pseudopot/'
 /
 &system
    a           =  1.64969e+01
    b           =  1.64809e+01
    c           =  5.00000e+01
    cosab       = -5.00000e-01
    degauss     =  1.00000e-02
    ecutrho     =  150
    ecutwfc     =  25
    ibrav       = 12
    nat         = 30
    ntyp        = 2
    occupations = 'smearing',
    smearing = 'gauss',
    degauss = 0.01
 /
 &electrons
    mixing_beta = 0.7
 /
 &IONS
	ion_dynamics = 'bfgs'
/

ATOMIC_SPECIES
C      12.01070  C.pbe-rrkjus.UPF
H       1.00794  H.pbe-rrkjus.UPF

ATOMIC_POSITIONS {angstrom}
C       3.759785   7.611155  14.310000
C       3.760673   9.047720  14.311500
C       2.543351   9.754656  14.318500
C       2.540098  11.162104  14.319500
C       4.977963   9.754085  14.308000
C       4.981391  11.161391  14.309500
C       1.295809  11.880316  14.324000
C       3.760766  11.862617  14.315500
C       6.225577  11.879459  14.306000
C      -6.953221  13.788314  14.301000
C      -4.488410  13.804585  14.308000
C       2.531580   0.233219  14.300500
C       2.534926   1.640667  14.296500
C      -2.023371  13.787029  14.320000
C       4.972708   0.232220  14.309500
C       4.969455   1.639668  14.307000
C       3.752380   2.346747  14.301000
C       3.753598   3.783312  14.299500
C       0.234245  12.489482  14.323000
C       3.757615   6.387113  14.301500
C       8.482504  13.178148  14.300000
C       3.755934   5.007354  14.298500
C      -0.961807  13.177863  14.321500
C       7.286753  12.489625  14.300000
H       1.602888   9.212001  14.325000
H       5.918147   9.210859  14.304000
H       3.761210  12.948498  14.315500
H      -4.488936  12.718847  14.312000
H       1.594577   2.183608  14.290000
H       5.909835   2.182466  14.310500

K_POINTS {crystal_c}
3
0.0000000000    0.0000000000    0.0000000000    10
0.0000000000    0.5000000000    0.0000000000    10
0.0000000000    0.5000000000    0.5000000000    10
```

## postprocess

```
&bands
prefix='PTEB'
outdir='tmp'
filband='PTEBband.dat'
plot_2d=.true.
/
```

## PTEBband.dat* will be obtained. It has the xk,yk, energy format


