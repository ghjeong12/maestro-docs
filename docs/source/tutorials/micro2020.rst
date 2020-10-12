.. _Tutorials:

======================================================================================================
MAESTRO Tutorial - `MICRO 2020 <https://www.microarch.org/micro53/>`_
======================================================================================================

MAESTRO: A Data-Centric Approach for Hardware and Mapping Explorations for Deep Learning Accelerators
----------------------------------------------------------------------------------------------------------------

Date: October 17, 2020

Organizers
------------------------------------
- `Tushar Krishna <https://tusharkrishna.ece.gatech.edu/>`_ (Georgia Tech)
- `Michael Pellauer <https://research.nvidia.com/person/michael-pellauer/>`_ (NVIDIA)
- `Hyoukjun Kwon <https://hyoukjunkwon.com/>`_ (Georgia Tech)
- `Prasanth Chatarasi <https://pchath.github.io/gatech-webpage/>`_ (Georgia Tech)
- `Geonhwa Jeong <https://ghjeong12.github.io/>`_ (Georgia Tech)
- `Sheng-Chun (Felix) Kao <https://hackmd.io/@felixkao/ryGUv1rbD>`_ (Georgia Tech)

Overview
------------------------------------

The efficiency of a deep neural network (DNN) accelerator depends on three factors—mapping, DNN layers, and hardware—constructing a extremely complicated design space of DNN accelerators. 
To demystify this design space and guide the DNN accelerator design for better efficiency, we present an analytical cost model,
MAESTRO (MICRO 2019 + IEEE Micro Top Picks 2020). MAESTRO receives the DNN model description, hardware resources
information, and mapping (described in a data-centric representation) as inputs. 
The data-centric representation consists of three directives that enable
concise description of mappings in a compiler-friendly form. 
MAESTRO analyzes various forms of data reuse in an accelerator based on inputs quickly and generates more than 20 statistics including total latency, energy, throughput, etc., as outputs. We also present various optimization tools for automated hardware design-space and mapping-space exploration enabled by MAESTRO’s fast analysis. 

Schedule (Eastern Time)
------------------------------------

=====================  ====================================================================== ================ ==================
**Time**                **Agenda**                                                              **Presenter**   **Resources**
10:00 - 10:05           **Welcome**                                                             Tushar          [Slides]
10:05 - 10:30           **DNN accelerators and dataflows**                                      Michael         [Slides]
\                       **MAESTRO Cost Model**                                                  \               \
10:30 - 11:00           Data-centric Mapping Directives                                         Hyoukjun        [Slides] [Video]
11:00 - 11:15           Analytical Cost Model                                                   Hyoukjun        [Slides] [Video]
11:15 - 11:45           Compiling and Running MAESTRO                                           Geonhwa         [Slides]
11:45 - 12:00           **Break**                                                               \               \
\                       **Automated Design-space Exploration using MAESTRO**                    \               \
12:00 - 12:15           Marvel: Mapping Space Exploration via Heuristics                        Prasanth        [Slides] [Video]
12:15 - 12:30           GAMMA: Mapping Space Exploration via Optimization                       Felix           [Slides]
12:30 - 12:45           ConfuciuX: Hardware Design-space Exploration via RL and Optimization    Felix           [Slides]
12:45 - 13:00           **Wrap Up**                                                             \               \
=====================  ====================================================================== ================ ==================

Resources
------------------------------------

- `MAESTRO Project GitHub <https://github.com/maestro-project>`_
- `MAESTRO Website <http://maestro.ece.gatech.edu/>`_
- `MAESTRO YouTube Channel <https://www.youtube.com/channel/UClWnx0maAai35n9TtRFfH0g/videos>`_

Papers
------------------------------------

1. MAESTRO Cost Model - MICRO 2019
2. Marvel - Arxiv
3. ConfuciuX - MICRO 2020
4. GAMMA - ICCAD 2020
