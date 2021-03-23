---
title: Tillägg – port-/regionsspecifika exempel
description: Den här artikeln visar enhetsspecifika exempel för ThreadX-moduler.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b54b8b094e608052fdbfc392d93a57ebb34515ed
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827402"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="c0a2a-103">Tillägg – port-/regionsspecifika exempel</span><span class="sxs-lookup"><span data-stu-id="c0a2a-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="c0a2a-104">ARM11-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="c0a2a-105">ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-106">Modulens inledning för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-107">Egenskaper för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="c0a2a-108">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-108">Bit</span></span> | <span data-ttu-id="c0a2a-109">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-109">Value</span></span> | <span data-ttu-id="c0a2a-110">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-111">[23-0]</span></span> | <span data-ttu-id="c0a2a-112">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-112">0</span></span> | <span data-ttu-id="c0a2a-113">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-113">Reserved</span></span>
| <span data-ttu-id="c0a2a-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-114">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-115">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-115">0x00</span></span><br /><span data-ttu-id="c0a2a-116">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-116">0x01</span></span><br /><span data-ttu-id="c0a2a-117">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-117">0x02</span></span> | <span data-ttu-id="c0a2a-118">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-118">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-119">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-119">IAR</span></span><br /><span data-ttu-id="c0a2a-120">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-120">ARM</span></span><br /><span data-ttu-id="c0a2a-121">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-122">Modul Länkar för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-123">Skapa moduler för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="c0a2a-124">Ett enkelt kommando rads exempel för att skapa en ARM11-modul med GCC:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-125">Tråd tilläggs definition för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-126">Skapa module Manager för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="c0a2a-127">Inget exempel har angetts.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="c0a2a-128">Attribut för extern minnes aktivering API för ARM11 med GCC</span><span class="sxs-lookup"><span data-stu-id="c0a2a-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="c0a2a-129">Den här funktionen är inte aktive rad på den här porten.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="c0a2a-130">ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-131">Modulens inledning för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-132">Egenskaper för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="c0a2a-133">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-133">Bit</span></span> | <span data-ttu-id="c0a2a-134">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-134">Value</span></span> | <span data-ttu-id="c0a2a-135">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-136">[23-0]</span></span> | <span data-ttu-id="c0a2a-137">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-137">0</span></span> | <span data-ttu-id="c0a2a-138">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-138">Reserved</span></span>
| <span data-ttu-id="c0a2a-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-139">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-140">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-140">0x00</span></span><br /><span data-ttu-id="c0a2a-141">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-141">0x01</span></span><br /><span data-ttu-id="c0a2a-142">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-142">0x02</span></span> | <span data-ttu-id="c0a2a-143">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-143">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-144">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-144">IAR</span></span><br /><span data-ttu-id="c0a2a-145">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-145">ARM</span></span><br /><span data-ttu-id="c0a2a-146">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-147">Modul Länkar för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="c0a2a-148">Ett exempel på en länkad fil som bygger på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-149">Skapa moduler för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="c0a2a-150">Ett enkelt kommando rads exempel för att skapa en ARM11-modul med AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-151">Tråd tilläggs definition för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-152">Skapa module Manager för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="c0a2a-153">Ett enkelt kommando rads exempel för att skapa en ARM11 module-hanterare med AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="c0a2a-154">Attribut för extern minnes aktivering API för ARM11 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="c0a2a-155">Den här funktionen är inte aktive rad på den här porten.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="c0a2a-156">Cortex – A7-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-157">Cortex – A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-158">Modulens inledning för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-159">Egenskaper för modulen för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="c0a2a-160">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-160">Bit</span></span> | <span data-ttu-id="c0a2a-161">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-161">Value</span></span> | <span data-ttu-id="c0a2a-162">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-163">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-163">0</span></span> | <span data-ttu-id="c0a2a-164">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-164">0</span></span><br /><span data-ttu-id="c0a2a-165">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-165">1</span></span> | <span data-ttu-id="c0a2a-166">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-166">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-167">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-167">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-168">[23-1]</span></span> | <span data-ttu-id="c0a2a-169">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-169">0</span></span> | <span data-ttu-id="c0a2a-170">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-170">Reserved</span></span>
| <span data-ttu-id="c0a2a-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-171">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-172">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-172">0x00</span></span><br /><span data-ttu-id="c0a2a-173">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-173">0x01</span></span><br /><span data-ttu-id="c0a2a-174">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-174">0x02</span></span> | <span data-ttu-id="c0a2a-175">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-175">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-176">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-176">IAR</span></span><br /><span data-ttu-id="c0a2a-177">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-177">ARM</span></span><br /><span data-ttu-id="c0a2a-178">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-179">Modul Länkar för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="c0a2a-180">Ett exempel på en länkad fil som bygger på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-181">Skapa moduler för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="c0a2a-182">Ett enkelt kommando rads exempel för att skapa en cortex-A7-modul med hjälp av AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-183">Tråd tilläggs definition för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-184">Skapa module Manager för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="c0a2a-185">Ett enkelt kommando rads exempel för att skapa en cortex-A7 module Manager med hjälp av AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="c0a2a-186">Attribut för externt minne Aktivera API för cortex-A7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="c0a2a-187">Följande attribut kan användas för att konfigurera inställningar för delat minne:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-187">The following attributes can be used to set up shared memory settings:</span></span>
| <span data-ttu-id="c0a2a-188">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-188">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-189">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="c0a2a-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="c0a2a-191">Kör aldrig</span><span class="sxs-lookup"><span data-stu-id="c0a2a-191">Execute Never</span></span> |
| <span data-ttu-id="c0a2a-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="c0a2a-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="c0a2a-193">B-inställning</span><span class="sxs-lookup"><span data-stu-id="c0a2a-193">B setting</span></span> |
| <span data-ttu-id="c0a2a-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="c0a2a-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="c0a2a-195">Inställningen C</span><span class="sxs-lookup"><span data-stu-id="c0a2a-195">C setting</span></span> |
| <span data-ttu-id="c0a2a-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="c0a2a-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="c0a2a-197">AP-inställning</span><span class="sxs-lookup"><span data-stu-id="c0a2a-197">AP setting</span></span> |
| <span data-ttu-id="c0a2a-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="c0a2a-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="c0a2a-199">TEX-inställning</span><span class="sxs-lookup"><span data-stu-id="c0a2a-199">TEX setting</span></span> |

<span data-ttu-id="c0a2a-200">Se ARM-dokumentationen för hur dessa inställningar konfigureras.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="c0a2a-201">Cortex-M3-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-202">Cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-203">Modulens inledning för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-204">Egenskaper för modulen för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="c0a2a-205">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-205">Bit</span></span> | <span data-ttu-id="c0a2a-206">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-206">Value</span></span> | <span data-ttu-id="c0a2a-207">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-208">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-208">0</span></span> | <span data-ttu-id="c0a2a-209">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-209">0</span></span><br /><span data-ttu-id="c0a2a-210">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-210">1</span></span> | <span data-ttu-id="c0a2a-211">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-211">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-212">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-212">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-213">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-213">1</span></span> | <span data-ttu-id="c0a2a-214">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-214">0</span></span><br /><span data-ttu-id="c0a2a-215">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-215">1</span></span> | <span data-ttu-id="c0a2a-216">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-216">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-217">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-218">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-218">2</span></span> | <span data-ttu-id="c0a2a-219">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-219">0</span></span><br /><span data-ttu-id="c0a2a-220">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-220">1</span></span> | <span data-ttu-id="c0a2a-221">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-222">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-223">[23-3]</span></span> | <span data-ttu-id="c0a2a-224">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-224">0</span></span> | <span data-ttu-id="c0a2a-225">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-225">Reserved</span></span>
| <span data-ttu-id="c0a2a-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-226">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-227">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-227">0x00</span></span><br /><span data-ttu-id="c0a2a-228">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-228">0x01</span></span><br /><span data-ttu-id="c0a2a-229">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-229">0x02</span></span> | <span data-ttu-id="c0a2a-230">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-230">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-231">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-231">IAR</span></span><br /><span data-ttu-id="c0a2a-232">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-232">ARM</span></span><br /><span data-ttu-id="c0a2a-233">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-234">Modul Länkar för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="c0a2a-235">Ingen exempel länks fil har angetts. länkning görs på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="c0a2a-236">Se nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-237">Skapa moduler för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="c0a2a-238">Ett exempel på ett build-skript har angetts:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-239">Tråd tilläggs definition för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-240">Skapa module Manager för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="c0a2a-241">Se exempel build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="c0a2a-242">Attribut för externt minne Aktivera API för cortex-m3 med AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="c0a2a-243">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-243">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-244">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-244">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-245">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-247">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-248">Cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-249">Modulens inledning för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-250">Egenskaper för modulen för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="c0a2a-251">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-251">Bit</span></span> | <span data-ttu-id="c0a2a-252">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-252">Value</span></span> | <span data-ttu-id="c0a2a-253">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-254">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-254">0</span></span> | <span data-ttu-id="c0a2a-255">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-255">0</span></span><br /><span data-ttu-id="c0a2a-256">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-256">1</span></span> | <span data-ttu-id="c0a2a-257">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-257">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-258">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-258">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-259">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-259">1</span></span> | <span data-ttu-id="c0a2a-260">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-260">0</span></span><br /><span data-ttu-id="c0a2a-261">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-261">1</span></span> | <span data-ttu-id="c0a2a-262">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-262">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-263">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-264">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-264">2</span></span> | <span data-ttu-id="c0a2a-265">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-265">0</span></span><br /><span data-ttu-id="c0a2a-266">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-266">1</span></span> | <span data-ttu-id="c0a2a-267">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-268">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-269">[23-3]</span></span> | <span data-ttu-id="c0a2a-270">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-270">0</span></span> | <span data-ttu-id="c0a2a-271">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-271">Reserved</span></span>
| <span data-ttu-id="c0a2a-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-272">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-273">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-273">0x00</span></span><br /><span data-ttu-id="c0a2a-274">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-274">0x01</span></span><br /><span data-ttu-id="c0a2a-275">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-275">0x02</span></span> | <span data-ttu-id="c0a2a-276">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-276">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-277">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-277">IAR</span></span><br /><span data-ttu-id="c0a2a-278">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-278">ARM</span></span><br /><span data-ttu-id="c0a2a-279">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-280">Modul Länkar för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="c0a2a-281">Ingen länknings fil används.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-281">No linker file is used.</span></span> <span data-ttu-id="c0a2a-282">Se projekt inställningar.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-283">Skapa moduler för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="c0a2a-284">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-284">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-285">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-286">Tråd tilläggs definition för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-287">Skapa module Manager för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="c0a2a-288">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-288">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-289">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="c0a2a-290">Attribut för externt minne Aktivera API för cortex-m3 med AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="c0a2a-291">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-291">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-292">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-292">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-293">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-295">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-296">Cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-297">Modulens inledning för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-298">Egenskaper för modulen för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="c0a2a-299">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-299">Bit</span></span> | <span data-ttu-id="c0a2a-300">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-300">Value</span></span> | <span data-ttu-id="c0a2a-301">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-302">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-302">0</span></span> | <span data-ttu-id="c0a2a-303">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-303">0</span></span><br /><span data-ttu-id="c0a2a-304">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-304">1</span></span> | <span data-ttu-id="c0a2a-305">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-305">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-306">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-306">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-307">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-307">1</span></span> | <span data-ttu-id="c0a2a-308">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-308">0</span></span><br /><span data-ttu-id="c0a2a-309">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-309">1</span></span> | <span data-ttu-id="c0a2a-310">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-310">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-311">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-312">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-312">2</span></span> | <span data-ttu-id="c0a2a-313">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-313">0</span></span><br /><span data-ttu-id="c0a2a-314">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-314">1</span></span> | <span data-ttu-id="c0a2a-315">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-316">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-317">[23-3]</span></span> | <span data-ttu-id="c0a2a-318">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-318">0</span></span> | <span data-ttu-id="c0a2a-319">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-319">Reserved</span></span>
| <span data-ttu-id="c0a2a-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-320">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-321">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-321">0x00</span></span><br /><span data-ttu-id="c0a2a-322">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-322">0x01</span></span><br /><span data-ttu-id="c0a2a-323">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-323">0x02</span></span> | <span data-ttu-id="c0a2a-324">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-324">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-325">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-325">IAR</span></span><br /><span data-ttu-id="c0a2a-326">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-326">ARM</span></span><br /><span data-ttu-id="c0a2a-327">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-328">Modul Länkar för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-329">Skapa moduler för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="c0a2a-330">Se build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-331">Tråd tilläggs definition för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-332">Skapa module Manager för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="c0a2a-333">Se build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="c0a2a-334">Attribut för externt minne Aktivera API för cortex-m3 med GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="c0a2a-335">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-335">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-336">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-336">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-337">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-339">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-340">Cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-341">Modulens inledning för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-342">Egenskaper för modulen för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="c0a2a-343">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-343">Bit</span></span> | <span data-ttu-id="c0a2a-344">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-344">Value</span></span> | <span data-ttu-id="c0a2a-345">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-346">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-346">0</span></span> | <span data-ttu-id="c0a2a-347">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-347">0</span></span><br /><span data-ttu-id="c0a2a-348">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-348">1</span></span> | <span data-ttu-id="c0a2a-349">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-349">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-350">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-350">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-351">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-351">1</span></span> | <span data-ttu-id="c0a2a-352">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-352">0</span></span><br /><span data-ttu-id="c0a2a-353">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-353">1</span></span> | <span data-ttu-id="c0a2a-354">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-354">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-355">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-356">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-356">2</span></span> | <span data-ttu-id="c0a2a-357">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-357">0</span></span><br /><span data-ttu-id="c0a2a-358">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-358">1</span></span> | <span data-ttu-id="c0a2a-359">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-360">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-361">[23-3]</span></span> | <span data-ttu-id="c0a2a-362">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-362">0</span></span> | <span data-ttu-id="c0a2a-363">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-363">Reserved</span></span>
| <span data-ttu-id="c0a2a-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-364">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-365">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-365">0x00</span></span><br /><span data-ttu-id="c0a2a-366">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-366">0x01</span></span><br /><span data-ttu-id="c0a2a-367">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-367">0x02</span></span> | <span data-ttu-id="c0a2a-368">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-368">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-369">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-369">IAR</span></span><br /><span data-ttu-id="c0a2a-370">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-370">ARM</span></span><br /><span data-ttu-id="c0a2a-371">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-372">Modul Länkar för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-373">Skapa moduler för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="c0a2a-374">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-374">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-375">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-376">Tråd tilläggs definition för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-377">Skapa module Manager för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="c0a2a-378">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-378">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-379">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="c0a2a-380">Attribut för externt minne Aktivera API för cortex-m3 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="c0a2a-381">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-381">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-382">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-382">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-383">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-385">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="c0a2a-386">Cortex – M33-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-387">Cortex – M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-388">Modulens inledning för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-389">Egenskaper för modulen för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="c0a2a-390">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-390">Bit</span></span> | <span data-ttu-id="c0a2a-391">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-391">Value</span></span> | <span data-ttu-id="c0a2a-392">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-393">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-393">0</span></span> | <span data-ttu-id="c0a2a-394">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-394">0</span></span><br /><span data-ttu-id="c0a2a-395">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-395">1</span></span> | <span data-ttu-id="c0a2a-396">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-396">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-397">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-397">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-398">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-398">1</span></span> | <span data-ttu-id="c0a2a-399">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-399">0</span></span><br /><span data-ttu-id="c0a2a-400">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-400">1</span></span> | <span data-ttu-id="c0a2a-401">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-401">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-402">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-403">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-403">2</span></span> | <span data-ttu-id="c0a2a-404">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-404">0</span></span><br /><span data-ttu-id="c0a2a-405">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-405">1</span></span> | <span data-ttu-id="c0a2a-406">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-407">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-408">[23-3]</span></span> | <span data-ttu-id="c0a2a-409">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-409">0</span></span> | <span data-ttu-id="c0a2a-410">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-410">Reserved</span></span>
| <span data-ttu-id="c0a2a-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-411">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-412">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-412">0x00</span></span><br /><span data-ttu-id="c0a2a-413">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-413">0x01</span></span><br /><span data-ttu-id="c0a2a-414">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-414">0x02</span></span> | <span data-ttu-id="c0a2a-415">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-415">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-416">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-416">IAR</span></span><br /><span data-ttu-id="c0a2a-417">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-417">ARM</span></span><br /><span data-ttu-id="c0a2a-418">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-419">Modul Länkar för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="c0a2a-420">Ingen länknings fil krävs för Keil verktygskedjan.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="c0a2a-421">Se versions inställningar i exempel projekt.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-421">See build settings in example project.</span></span>
<span data-ttu-id="c0a2a-422">Viktiga länknings alternativ visas nedan:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-423">Skapa moduler för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="c0a2a-424">Kompilator inställningar:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-425">Tråd tilläggs definition för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-426">Skapa module Manager för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="c0a2a-427">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-427">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-428">Bygg biblioteket ThreadX, ThreadX modules, sample_threadx_module Project och demo_threadx_non secure_zone Project.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="c0a2a-429">Attribut för externt minne Aktivera API för cortex-M33 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="c0a2a-430">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="c0a2a-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="c0a2a-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="c0a2a-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-436">Cortex – M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-437">Modulens inledning för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-438">Egenskaper för modulen för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="c0a2a-439">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-439">Bit</span></span> | <span data-ttu-id="c0a2a-440">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-440">Value</span></span> | <span data-ttu-id="c0a2a-441">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-442">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-442">0</span></span> | <span data-ttu-id="c0a2a-443">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-443">0</span></span><br /><span data-ttu-id="c0a2a-444">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-444">1</span></span> | <span data-ttu-id="c0a2a-445">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-445">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-446">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-446">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-447">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-447">1</span></span> | <span data-ttu-id="c0a2a-448">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-448">0</span></span><br /><span data-ttu-id="c0a2a-449">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-449">1</span></span> | <span data-ttu-id="c0a2a-450">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-450">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-451">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-452">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-452">2</span></span> | <span data-ttu-id="c0a2a-453">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-453">0</span></span><br /><span data-ttu-id="c0a2a-454">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-454">1</span></span> | <span data-ttu-id="c0a2a-455">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-456">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-457">[23-3]</span></span> | <span data-ttu-id="c0a2a-458">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-458">0</span></span> | <span data-ttu-id="c0a2a-459">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-459">Reserved</span></span>
| <span data-ttu-id="c0a2a-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-460">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-461">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-461">0x00</span></span><br /><span data-ttu-id="c0a2a-462">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-462">0x01</span></span><br /><span data-ttu-id="c0a2a-463">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-463">0x02</span></span> | <span data-ttu-id="c0a2a-464">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-464">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-465">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-465">IAR</span></span><br /><span data-ttu-id="c0a2a-466">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-466">ARM</span></span><br /><span data-ttu-id="c0a2a-467">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-468">Modul Länkar för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-469">Skapa moduler för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-470">Tråd tilläggs definition för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-471">Skapa module Manager för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="c0a2a-472">Attribut för externt minne Aktivera API för cortex-M33 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="c0a2a-473">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="c0a2a-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="c0a2a-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="c0a2a-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-479">Cortex – M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-480">Modulens inledning för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-481">Egenskaper för modulen för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="c0a2a-482">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-482">Bit</span></span> | <span data-ttu-id="c0a2a-483">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-483">Value</span></span> | <span data-ttu-id="c0a2a-484">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-485">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-485">0</span></span> | <span data-ttu-id="c0a2a-486">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-486">0</span></span><br /><span data-ttu-id="c0a2a-487">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-487">1</span></span> | <span data-ttu-id="c0a2a-488">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-488">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-489">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-489">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-490">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-490">1</span></span> | <span data-ttu-id="c0a2a-491">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-491">0</span></span><br /><span data-ttu-id="c0a2a-492">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-492">1</span></span> | <span data-ttu-id="c0a2a-493">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-493">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-494">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-495">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-495">2</span></span> | <span data-ttu-id="c0a2a-496">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-496">0</span></span><br /><span data-ttu-id="c0a2a-497">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-497">1</span></span> | <span data-ttu-id="c0a2a-498">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-499">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-500">[23-3]</span></span> | <span data-ttu-id="c0a2a-501">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-501">0</span></span> | <span data-ttu-id="c0a2a-502">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-502">Reserved</span></span>
| <span data-ttu-id="c0a2a-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-503">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-504">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-504">0x00</span></span><br /><span data-ttu-id="c0a2a-505">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-505">0x01</span></span><br /><span data-ttu-id="c0a2a-506">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-506">0x02</span></span> | <span data-ttu-id="c0a2a-507">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-507">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-508">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-508">IAR</span></span><br /><span data-ttu-id="c0a2a-509">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-509">ARM</span></span><br /><span data-ttu-id="c0a2a-510">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-511">Modul Länkar för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-512">Skapa moduler för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-513">Tråd tilläggs definition för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-514">Skapa module Manager för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="c0a2a-515">En exempel arbets yta har ännu inte tillhandahållits.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="c0a2a-516">Kommer snart.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="c0a2a-517">Attribut för externt minne Aktivera API för cortex-M33 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="c0a2a-518">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="c0a2a-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="c0a2a-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="c0a2a-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="c0a2a-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="c0a2a-524">Cortex – M4-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-525">Cortex – M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-526">Modulens inledning för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-527">Egenskaper för modulen för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="c0a2a-528">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-528">Bit</span></span> | <span data-ttu-id="c0a2a-529">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-529">Value</span></span> | <span data-ttu-id="c0a2a-530">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-531">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-531">0</span></span> | <span data-ttu-id="c0a2a-532">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-532">0</span></span><br /><span data-ttu-id="c0a2a-533">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-533">1</span></span> | <span data-ttu-id="c0a2a-534">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-534">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-535">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-535">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-536">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-536">1</span></span> | <span data-ttu-id="c0a2a-537">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-537">0</span></span><br /><span data-ttu-id="c0a2a-538">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-538">1</span></span> | <span data-ttu-id="c0a2a-539">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-539">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-540">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-541">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-541">2</span></span> | <span data-ttu-id="c0a2a-542">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-542">0</span></span><br /><span data-ttu-id="c0a2a-543">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-543">1</span></span> | <span data-ttu-id="c0a2a-544">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-545">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-546">[23-3]</span></span> | <span data-ttu-id="c0a2a-547">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-547">0</span></span> | <span data-ttu-id="c0a2a-548">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-548">Reserved</span></span>
| <span data-ttu-id="c0a2a-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-549">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-550">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-550">0x00</span></span><br /><span data-ttu-id="c0a2a-551">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-551">0x01</span></span><br /><span data-ttu-id="c0a2a-552">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-552">0x02</span></span> | <span data-ttu-id="c0a2a-553">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-553">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-554">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-554">IAR</span></span><br /><span data-ttu-id="c0a2a-555">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-555">ARM</span></span><br /><span data-ttu-id="c0a2a-556">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-557">Modul Länkar för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="c0a2a-558">Ingen exempel länks fil har angetts. länkning görs på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="c0a2a-559">Se nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-560">Skapa moduler för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="c0a2a-561">Se exempel build_threadx_module_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-562">Tråd tilläggs definition för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-563">Skapa module Manager för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="c0a2a-564">Se exempel build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="c0a2a-565">Attribut för externt minne Aktivera API för cortex-M4 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="c0a2a-566">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-566">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-567">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-567">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-568">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-570">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-571">Cortex – M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-572">Modulens inledning för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-573">Egenskaper för modulen för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="c0a2a-574">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-574">Bit</span></span> | <span data-ttu-id="c0a2a-575">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-575">Value</span></span> | <span data-ttu-id="c0a2a-576">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-577">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-577">0</span></span> | <span data-ttu-id="c0a2a-578">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-578">0</span></span><br /><span data-ttu-id="c0a2a-579">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-579">1</span></span> | <span data-ttu-id="c0a2a-580">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-580">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-581">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-581">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-582">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-582">1</span></span> | <span data-ttu-id="c0a2a-583">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-583">0</span></span><br /><span data-ttu-id="c0a2a-584">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-584">1</span></span> | <span data-ttu-id="c0a2a-585">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-585">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-586">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-587">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-587">2</span></span> | <span data-ttu-id="c0a2a-588">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-588">0</span></span><br /><span data-ttu-id="c0a2a-589">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-589">1</span></span> | <span data-ttu-id="c0a2a-590">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-591">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-592">[23-3]</span></span> | <span data-ttu-id="c0a2a-593">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-593">0</span></span> | <span data-ttu-id="c0a2a-594">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-594">Reserved</span></span>
| <span data-ttu-id="c0a2a-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-595">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-596">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-596">0x00</span></span><br /><span data-ttu-id="c0a2a-597">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-597">0x01</span></span><br /><span data-ttu-id="c0a2a-598">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-598">0x02</span></span> | <span data-ttu-id="c0a2a-599">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-599">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-600">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-600">IAR</span></span><br /><span data-ttu-id="c0a2a-601">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-601">ARM</span></span><br /><span data-ttu-id="c0a2a-602">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-603">Modul Länkar för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="c0a2a-604">Ingen länknings fil används.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-604">No linker file is used.</span></span> <span data-ttu-id="c0a2a-605">Se projekt inställningar.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-606">Skapa moduler för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="c0a2a-607">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-607">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-608">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-609">Tråd tilläggs definition för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-610">Skapa module Manager för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="c0a2a-611">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-611">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-612">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="c0a2a-613">Attribut för externt minne Aktivera API för cortex-M4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="c0a2a-614">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-614">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-615">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-615">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-616">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-618">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-619">Cortex – M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-620">Modulens inledning för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-621">Egenskaper för modulen för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="c0a2a-622">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-622">Bit</span></span> | <span data-ttu-id="c0a2a-623">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-623">Value</span></span> | <span data-ttu-id="c0a2a-624">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-625">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-625">0</span></span> | <span data-ttu-id="c0a2a-626">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-626">0</span></span><br /><span data-ttu-id="c0a2a-627">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-627">1</span></span> | <span data-ttu-id="c0a2a-628">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-628">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-629">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-629">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-630">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-630">1</span></span> | <span data-ttu-id="c0a2a-631">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-631">0</span></span><br /><span data-ttu-id="c0a2a-632">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-632">1</span></span> | <span data-ttu-id="c0a2a-633">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-633">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-634">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-635">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-635">2</span></span> | <span data-ttu-id="c0a2a-636">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-636">0</span></span><br /><span data-ttu-id="c0a2a-637">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-637">1</span></span> | <span data-ttu-id="c0a2a-638">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-639">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-640">[23-3]</span></span> | <span data-ttu-id="c0a2a-641">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-641">0</span></span> | <span data-ttu-id="c0a2a-642">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-642">Reserved</span></span>
| <span data-ttu-id="c0a2a-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-643">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-644">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-644">0x00</span></span><br /><span data-ttu-id="c0a2a-645">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-645">0x01</span></span><br /><span data-ttu-id="c0a2a-646">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-646">0x02</span></span> | <span data-ttu-id="c0a2a-647">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-647">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-648">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-648">IAR</span></span><br /><span data-ttu-id="c0a2a-649">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-649">ARM</span></span><br /><span data-ttu-id="c0a2a-650">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-651">Modul Länkar för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-652">Skapa moduler för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="c0a2a-653">Se build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-654">Tråd tilläggs definition för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-655">Skapa module Manager för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="c0a2a-656">Se build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="c0a2a-657">Attribut för externt minne Aktivera API för cortex-M4 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="c0a2a-658">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-658">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-659">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-659">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-660">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-662">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-663">Cortex – M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-664">Modulens inledning för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-665">Egenskaper för modulen för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="c0a2a-666">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-666">Bit</span></span> | <span data-ttu-id="c0a2a-667">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-667">Value</span></span> | <span data-ttu-id="c0a2a-668">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-669">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-669">0</span></span> | <span data-ttu-id="c0a2a-670">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-670">0</span></span><br /><span data-ttu-id="c0a2a-671">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-671">1</span></span> | <span data-ttu-id="c0a2a-672">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-672">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-673">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-673">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-674">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-674">1</span></span> | <span data-ttu-id="c0a2a-675">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-675">0</span></span><br /><span data-ttu-id="c0a2a-676">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-676">1</span></span> | <span data-ttu-id="c0a2a-677">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-677">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-678">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-679">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-679">2</span></span> | <span data-ttu-id="c0a2a-680">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-680">0</span></span><br /><span data-ttu-id="c0a2a-681">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-681">1</span></span> | <span data-ttu-id="c0a2a-682">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-683">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-684">[23-3]</span></span> | <span data-ttu-id="c0a2a-685">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-685">0</span></span> | <span data-ttu-id="c0a2a-686">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-686">Reserved</span></span>
| <span data-ttu-id="c0a2a-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-687">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-688">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-688">0x00</span></span><br /><span data-ttu-id="c0a2a-689">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-689">0x01</span></span><br /><span data-ttu-id="c0a2a-690">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-690">0x02</span></span> | <span data-ttu-id="c0a2a-691">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-691">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-692">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-692">IAR</span></span><br /><span data-ttu-id="c0a2a-693">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-693">ARM</span></span><br /><span data-ttu-id="c0a2a-694">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-695">Modul Länkar för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-696">Skapa moduler för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="c0a2a-697">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-697">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-698">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-699">Tråd tilläggs definition för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-700">Skapa module Manager för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="c0a2a-701">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-701">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-702">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="c0a2a-703">Attribut för externt minne Aktivera API för cortex-M4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="c0a2a-704">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-704">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-705">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-705">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-706">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-708">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="c0a2a-709">Cortex – M7-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-710">Cortex – M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-711">Modulens inledning för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-712">Egenskaper för modulen för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="c0a2a-713">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-713">Bit</span></span> | <span data-ttu-id="c0a2a-714">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-714">Value</span></span> | <span data-ttu-id="c0a2a-715">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-716">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-716">0</span></span> | <span data-ttu-id="c0a2a-717">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-717">0</span></span><br /><span data-ttu-id="c0a2a-718">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-718">1</span></span> | <span data-ttu-id="c0a2a-719">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-719">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-720">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-720">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-721">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-721">1</span></span> | <span data-ttu-id="c0a2a-722">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-722">0</span></span><br /><span data-ttu-id="c0a2a-723">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-723">1</span></span> | <span data-ttu-id="c0a2a-724">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-724">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-725">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-726">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-726">2</span></span> | <span data-ttu-id="c0a2a-727">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-727">0</span></span><br /><span data-ttu-id="c0a2a-728">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-728">1</span></span> | <span data-ttu-id="c0a2a-729">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-730">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-731">[23-3]</span></span> | <span data-ttu-id="c0a2a-732">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-732">0</span></span> | <span data-ttu-id="c0a2a-733">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-733">Reserved</span></span>
| <span data-ttu-id="c0a2a-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-734">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-735">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-735">0x00</span></span><br /><span data-ttu-id="c0a2a-736">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-736">0x01</span></span><br /><span data-ttu-id="c0a2a-737">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-737">0x02</span></span> | <span data-ttu-id="c0a2a-738">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-738">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-739">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-739">IAR</span></span><br /><span data-ttu-id="c0a2a-740">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-740">ARM</span></span><br /><span data-ttu-id="c0a2a-741">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-742">Modul Länkar för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="c0a2a-743">Ett exempel på en länkad fil som bygger på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-744">Skapa moduler för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="c0a2a-745">Ett enkelt kommando rads exempel för att skapa en cortex-M7-modul med hjälp av AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-746">Tråd tilläggs definition för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-747">Skapa module Manager för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="c0a2a-748">Ett enkelt kommando rads exempel för att skapa en cortex-M7 module Manager med hjälp av AC5:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="c0a2a-749">Attribut för externt minne Aktivera API för cortex-M7 med hjälp av AC5</span><span class="sxs-lookup"><span data-stu-id="c0a2a-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-750">Cortex – M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-751">Egenskaper för modulen för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="c0a2a-752">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-752">Bit</span></span> | <span data-ttu-id="c0a2a-753">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-753">Value</span></span> | <span data-ttu-id="c0a2a-754">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-755">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-755">0</span></span> | <span data-ttu-id="c0a2a-756">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-756">0</span></span><br /><span data-ttu-id="c0a2a-757">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-757">1</span></span> | <span data-ttu-id="c0a2a-758">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-758">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-759">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-759">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-760">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-760">1</span></span> | <span data-ttu-id="c0a2a-761">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-761">0</span></span><br /><span data-ttu-id="c0a2a-762">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-762">1</span></span> | <span data-ttu-id="c0a2a-763">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-763">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-764">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-765">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-765">2</span></span> | <span data-ttu-id="c0a2a-766">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-766">0</span></span><br /><span data-ttu-id="c0a2a-767">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-767">1</span></span> | <span data-ttu-id="c0a2a-768">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-769">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-770">[23-3]</span></span> | <span data-ttu-id="c0a2a-771">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-771">0</span></span> | <span data-ttu-id="c0a2a-772">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-772">Reserved</span></span>
| <span data-ttu-id="c0a2a-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-773">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-774">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-774">0x00</span></span><br /><span data-ttu-id="c0a2a-775">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-775">0x01</span></span><br /><span data-ttu-id="c0a2a-776">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-776">0x02</span></span> | <span data-ttu-id="c0a2a-777">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-777">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-778">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-778">IAR</span></span><br /><span data-ttu-id="c0a2a-779">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-779">ARM</span></span><br /><span data-ttu-id="c0a2a-780">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-781">Modul Länkar för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="c0a2a-782">Ingen länknings fil används.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-782">No linker file is used.</span></span> <span data-ttu-id="c0a2a-783">Se projekt inställningar.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-784">Skapa moduler för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="c0a2a-785">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-785">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-786">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-787">Tråd tilläggs definition för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-788">Skapa module Manager för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="c0a2a-789">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-789">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-790">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, projektmodulen och exempel module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="c0a2a-791">Attribut för externt minne Aktivera API för cortex-M7 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="c0a2a-792">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-792">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-793">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-793">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-794">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-796">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-797">Cortex – M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-798">Egenskaper för modulen för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="c0a2a-799">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-799">Bit</span></span> | <span data-ttu-id="c0a2a-800">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-800">Value</span></span> | <span data-ttu-id="c0a2a-801">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-802">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-802">0</span></span> | <span data-ttu-id="c0a2a-803">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-803">0</span></span><br /><span data-ttu-id="c0a2a-804">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-804">1</span></span> | <span data-ttu-id="c0a2a-805">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-805">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-806">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-806">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-807">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-807">1</span></span> | <span data-ttu-id="c0a2a-808">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-808">0</span></span><br /><span data-ttu-id="c0a2a-809">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-809">1</span></span> | <span data-ttu-id="c0a2a-810">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-810">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-811">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-812">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-812">2</span></span> | <span data-ttu-id="c0a2a-813">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-813">0</span></span><br /><span data-ttu-id="c0a2a-814">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-814">1</span></span> | <span data-ttu-id="c0a2a-815">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-816">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-817">[23-3]</span></span> | <span data-ttu-id="c0a2a-818">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-818">0</span></span> | <span data-ttu-id="c0a2a-819">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-819">Reserved</span></span>
| <span data-ttu-id="c0a2a-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-820">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-821">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-821">0x00</span></span><br /><span data-ttu-id="c0a2a-822">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-822">0x01</span></span><br /><span data-ttu-id="c0a2a-823">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-823">0x02</span></span> | <span data-ttu-id="c0a2a-824">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-824">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-825">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-825">IAR</span></span><br /><span data-ttu-id="c0a2a-826">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-826">ARM</span></span><br /><span data-ttu-id="c0a2a-827">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-828">Modul Länkar för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-829">Skapa moduler för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="c0a2a-830">Se build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-831">Tråd tilläggs definition för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-832">Skapa module Manager för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="c0a2a-833">Se build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="c0a2a-834">Attribut för externt minne Aktivera API för cortex-M7 med hjälp av GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="c0a2a-835">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-835">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-836">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-836">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-837">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-839">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-840">Cortex – M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-841">Modulens inledning för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-842">Egenskaper för modulen för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="c0a2a-843">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-843">Bit</span></span> | <span data-ttu-id="c0a2a-844">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-844">Value</span></span> | <span data-ttu-id="c0a2a-845">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-846">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-846">0</span></span> | <span data-ttu-id="c0a2a-847">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-847">0</span></span><br /><span data-ttu-id="c0a2a-848">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-848">1</span></span> | <span data-ttu-id="c0a2a-849">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-849">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-850">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-850">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-851">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-851">1</span></span> | <span data-ttu-id="c0a2a-852">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-852">0</span></span><br /><span data-ttu-id="c0a2a-853">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-853">1</span></span> | <span data-ttu-id="c0a2a-854">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-854">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-855">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-856">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-856">2</span></span> | <span data-ttu-id="c0a2a-857">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-857">0</span></span><br /><span data-ttu-id="c0a2a-858">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-858">1</span></span> | <span data-ttu-id="c0a2a-859">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-860">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-861">[23-3]</span></span> | <span data-ttu-id="c0a2a-862">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-862">0</span></span> | <span data-ttu-id="c0a2a-863">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-863">Reserved</span></span>
| <span data-ttu-id="c0a2a-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-864">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-865">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-865">0x00</span></span><br /><span data-ttu-id="c0a2a-866">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-866">0x01</span></span><br /><span data-ttu-id="c0a2a-867">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-867">0x02</span></span> | <span data-ttu-id="c0a2a-868">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-868">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-869">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-869">IAR</span></span><br /><span data-ttu-id="c0a2a-870">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-870">ARM</span></span><br /><span data-ttu-id="c0a2a-871">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-872">Modul Länkar för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-873">Skapa moduler för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="c0a2a-874">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-874">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-875">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-876">Tråd tilläggs definition för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-877">Skapa module Manager för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="c0a2a-878">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-878">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-879">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="c0a2a-880">Attribut för externt minne Aktivera API för cortex-M7 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="c0a2a-881">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-881">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-882">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-882">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-883">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-885">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="c0a2a-886">Cortex – R4-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-887">Cortex – R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-888">Modulens inledning för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-889">Egenskaper för modulen för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="c0a2a-890">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-890">Bit</span></span> | <span data-ttu-id="c0a2a-891">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-891">Value</span></span> | <span data-ttu-id="c0a2a-892">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-893">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-893">0</span></span> | <span data-ttu-id="c0a2a-894">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-894">0</span></span><br /><span data-ttu-id="c0a2a-895">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-895">1</span></span> | <span data-ttu-id="c0a2a-896">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-896">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-897">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-897">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-898">[23-1]</span></span> | <span data-ttu-id="c0a2a-899">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-899">0</span></span> | <span data-ttu-id="c0a2a-900">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-900">Reserved</span></span>
| <span data-ttu-id="c0a2a-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-901">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-902">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-902">0x00</span></span><br /><span data-ttu-id="c0a2a-903">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-903">0x01</span></span><br /><span data-ttu-id="c0a2a-904">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-904">0x02</span></span> | <span data-ttu-id="c0a2a-905">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-905">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-906">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-906">IAR</span></span><br /><span data-ttu-id="c0a2a-907">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-907">ARM</span></span><br /><span data-ttu-id="c0a2a-908">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-909">Modul Länkar för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="c0a2a-910">Ett exempel på en länkad fil som bygger på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-911">Skapa moduler för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="c0a2a-912">Ett enkelt kommando rads exempel för att skapa en cortex-R4-modul med hjälp av AC6:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-913">Tråd tilläggs definition för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-914">Skapa module Manager för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="c0a2a-915">Ett enkelt kommando rads exempel för att skapa en cortex-R4 module Manager med hjälp av AC6:</span><span class="sxs-lookup"><span data-stu-id="c0a2a-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="c0a2a-916">Attribut för externt minne Aktivera API för cortex-R4 med hjälp av AC6</span><span class="sxs-lookup"><span data-stu-id="c0a2a-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="c0a2a-917">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-917">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-918">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-918">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-919">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-921">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-922">Cortex – R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-923">Modulens inledning för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-924">Egenskaper för modulen för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="c0a2a-925">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-925">Bit</span></span> | <span data-ttu-id="c0a2a-926">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-926">Value</span></span> | <span data-ttu-id="c0a2a-927">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-928">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-928">0</span></span> | <span data-ttu-id="c0a2a-929">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-929">0</span></span><br /><span data-ttu-id="c0a2a-930">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-930">1</span></span> | <span data-ttu-id="c0a2a-931">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-931">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-932">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-932">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-933">[23-1]</span></span> | <span data-ttu-id="c0a2a-934">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-934">0</span></span> | <span data-ttu-id="c0a2a-935">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-935">Reserved</span></span>
| <span data-ttu-id="c0a2a-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-936">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-937">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-937">0x00</span></span><br /><span data-ttu-id="c0a2a-938">0x01</span><span class="sxs-lookup"><span data-stu-id="c0a2a-938">0x01</span></span><br /><span data-ttu-id="c0a2a-939">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-939">0x02</span></span> | <span data-ttu-id="c0a2a-940">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-940">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-941">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-941">IAR</span></span><br /><span data-ttu-id="c0a2a-942">ARM</span><span class="sxs-lookup"><span data-stu-id="c0a2a-942">ARM</span></span><br /><span data-ttu-id="c0a2a-943">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-944">Modul Länkar för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-945">Skapa moduler för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="c0a2a-946">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-946">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-947">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-948">Tråd tilläggs definition för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-949">Skapa module Manager för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="c0a2a-950">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-950">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-951">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="c0a2a-952">Attribut för externt minne Aktivera API för cortex-R4 med hjälp av IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="c0a2a-953">Modulen har alltid Läs behörighet till delat minne.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-953">Module always has read access to shared memory.</span></span>
| <span data-ttu-id="c0a2a-954">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-954">Attribute parameter</span></span> | <span data-ttu-id="c0a2a-955">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-957">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="c0a2a-958">MCF544xx-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-959">MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-960">Modulens inledning för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-961">Egenskaper för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="c0a2a-962">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-962">Bit</span></span> | <span data-ttu-id="c0a2a-963">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-963">Value</span></span> | <span data-ttu-id="c0a2a-964">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-965">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-965">0</span></span> | <span data-ttu-id="c0a2a-966">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-966">0</span></span><br /><span data-ttu-id="c0a2a-967">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-967">1</span></span> | <span data-ttu-id="c0a2a-968">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-968">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-969">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-969">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-970">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-970">1</span></span> | <span data-ttu-id="c0a2a-971">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-971">0</span></span><br /><span data-ttu-id="c0a2a-972">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-972">1</span></span> | <span data-ttu-id="c0a2a-973">Inget MMU skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-973">No MMU protection</span></span><br /><span data-ttu-id="c0a2a-974">MMU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-975">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-975">2</span></span> | <span data-ttu-id="c0a2a-976">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-976">0</span></span><br /><span data-ttu-id="c0a2a-977">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-977">1</span></span> | <span data-ttu-id="c0a2a-978">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-979">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-980">[23-3]</span></span> | <span data-ttu-id="c0a2a-981">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-981">0</span></span> | <span data-ttu-id="c0a2a-982">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-982">Reserved</span></span>
| <span data-ttu-id="c0a2a-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-983">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-984">0x03</span><span class="sxs-lookup"><span data-stu-id="c0a2a-984">0x03</span></span> | <span data-ttu-id="c0a2a-985">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-985">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-986">GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-987">Modul Länkar för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-988">Skapa moduler för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="c0a2a-989">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-989">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-990">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-991">Tråd tilläggs definition för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-992">Skapa module Manager för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="c0a2a-993">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-993">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-994">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="c0a2a-995">Attribut för extern minnes aktivering API för MCF544xx med GHS</span><span class="sxs-lookup"><span data-stu-id="c0a2a-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="c0a2a-996">Den här funktionen är inte aktive rad på MCF544xx.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="c0a2a-997">RX63-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="c0a2a-998">RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-999">Modulens inledning för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-1000">Egenskaper för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="c0a2a-1001">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1001">Bit</span></span> | <span data-ttu-id="c0a2a-1002">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1002">Value</span></span> | <span data-ttu-id="c0a2a-1003">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-1004">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1004">0</span></span> | <span data-ttu-id="c0a2a-1005">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1005">0</span></span><br /><span data-ttu-id="c0a2a-1006">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1006">1</span></span> | <span data-ttu-id="c0a2a-1007">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1007">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-1008">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1008">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-1009">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1009">1</span></span> | <span data-ttu-id="c0a2a-1010">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1010">0</span></span><br /><span data-ttu-id="c0a2a-1011">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1011">1</span></span> | <span data-ttu-id="c0a2a-1012">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1012">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-1013">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-1014">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1014">2</span></span> | <span data-ttu-id="c0a2a-1015">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1015">0</span></span><br /><span data-ttu-id="c0a2a-1016">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1016">1</span></span> | <span data-ttu-id="c0a2a-1017">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-1018">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1019">[23-3]</span></span> | <span data-ttu-id="c0a2a-1020">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1020">0</span></span> | <span data-ttu-id="c0a2a-1021">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1021">Reserved</span></span>
| <span data-ttu-id="c0a2a-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1022">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1023">0x00</span></span><br /><span data-ttu-id="c0a2a-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1024">0x02</span></span> | <span data-ttu-id="c0a2a-1025">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1025">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1026">IAR</span></span><br /><span data-ttu-id="c0a2a-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-1028">Modul Länkar för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-1029">Skapa moduler för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="c0a2a-1030">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1030">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-1031">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="c0a2a-1032">Tråd tilläggs definition för RXRX635N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-1033">Skapa module Manager för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="c0a2a-1034">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1034">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-1035">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="c0a2a-1036">Attribut för extern minnes aktivering API för RX63 med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="c0a2a-1037">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1037">Attribute Parameter</span></span> | <span data-ttu-id="c0a2a-1038">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="c0a2a-1040">Kör kod</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1040">Execute code</span></span> |
| <span data-ttu-id="c0a2a-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-1042">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1042">Write access</span></span> |
| <span data-ttu-id="c0a2a-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="c0a2a-1044">Läsbehörighet</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="c0a2a-1045">RX65N-processor</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="c0a2a-1046">RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1047">Modulens inledning för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1048">Egenskaper för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="c0a2a-1049">Bitmask</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1049">Bit</span></span> | <span data-ttu-id="c0a2a-1050">Värde</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1050">Value</span></span> | <span data-ttu-id="c0a2a-1051">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="c0a2a-1052">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1052">0</span></span> | <span data-ttu-id="c0a2a-1053">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1053">0</span></span><br /><span data-ttu-id="c0a2a-1054">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1054">1</span></span> | <span data-ttu-id="c0a2a-1055">Körning av privilegierat läge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1055">Privileged mode execution</span></span><br /><span data-ttu-id="c0a2a-1056">Körning av användarläge</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1056">User mode execution</span></span> |
| <span data-ttu-id="c0a2a-1057">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1057">1</span></span> | <span data-ttu-id="c0a2a-1058">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1058">0</span></span><br /><span data-ttu-id="c0a2a-1059">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1059">1</span></span> | <span data-ttu-id="c0a2a-1060">Inget MPU-skydd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1060">No MPU protection</span></span><br /><span data-ttu-id="c0a2a-1061">MPU-skydd (användar läge måste vara valt)</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="c0a2a-1062">2</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1062">2</span></span> | <span data-ttu-id="c0a2a-1063">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1063">0</span></span><br /><span data-ttu-id="c0a2a-1064">1</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1064">1</span></span> | <span data-ttu-id="c0a2a-1065">Inaktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="c0a2a-1066">Aktivera delad/extern minnes åtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="c0a2a-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1067">[23-3]</span></span> | <span data-ttu-id="c0a2a-1068">0</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1068">0</span></span> | <span data-ttu-id="c0a2a-1069">Reserverat</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1069">Reserved</span></span>
| <span data-ttu-id="c0a2a-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1070">[31-24]</span></span> | <br /><span data-ttu-id="c0a2a-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1071">0x00</span></span><br /><span data-ttu-id="c0a2a-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1072">0x02</span></span> | <span data-ttu-id="c0a2a-1073">**Kompilator-ID**</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1073">**Compiler ID**</span></span><br /><span data-ttu-id="c0a2a-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1074">IAR</span></span><br /><span data-ttu-id="c0a2a-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1076">Modul Länkar för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1077">Skapa moduler för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="c0a2a-1078">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1078">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-1079">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1080">Tråd tilläggs definition för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1081">Skapa module Manager för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="c0a2a-1082">En exempel arbets yta tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1082">An example workspace is provided.</span></span> <span data-ttu-id="c0a2a-1083">Bygg ThreadX-biblioteket, ThreadX modules-biblioteket, demo module-projektet och demo module Manager-projektet.</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="c0a2a-1084">Attribut för extern minnes aktivering API för RX65N med IAR</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="c0a2a-1085">Attribute-parameter</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1085">Attribute Parameter</span></span> | <span data-ttu-id="c0a2a-1086">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="c0a2a-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="c0a2a-1088">Kör kod</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1088">Execute code</span></span> |
| <span data-ttu-id="c0a2a-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="c0a2a-1090">Skrivåtkomst</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1090">Write access</span></span> |
| <span data-ttu-id="c0a2a-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="c0a2a-1092">Läsbehörighet</span><span class="sxs-lookup"><span data-stu-id="c0a2a-1092">Read access</span></span> |
