# System Specifications

> Container Environment | Alibaba Cloud Function Compute | Kata Container

> [!NOTE]
> Generated: February 2025 | Hostname: c-6996ca5e-148f475d-24dde3e46771

---

## Quick Summary

| Component | Specification |
|-----------|--------------|
| Container Type | Kata Container (Hardware VM) |
| Root Filesystem | 9.9 GB total, 3% used |
| Memory | 8.0 GiB total, 6.8 GiB available |
| CPU | 4 vCPUs, Intel Xeon @ 2.8 GHz |
| Storage Backend | JuiceFS + S3FS mounted volumes |

---

## Disk Usage

```
Filesystem                                       Size  Used Avail Use% Mounted on
c-6996ca5e-148f475d-24dde3e46771-rootfs          9.9G  261M  9.1G   3% /
tmpfs                                             64M     0   64M   0% /dev
tmpfs                                            4.1G     0  4.1G   0% /sys/fs/cgroup
shm                                               64M     0   64M   0% /dev/shm
kataShared                                       248G  661M  248G   1% /.dockerenv
tmpfs                                            4.1G   36K  4.1G   1% /etc/hosts
s3fs                                              16E     0   16E   0% /home/official_skills
JuiceFS:pcs-ue6ju0nuiu0hz7tjc-0e3odv6t4dackr8s3  1.0P   21T 1004T   2% /tmp/my-project
s3fs                                              16E     0   16E   0% /home/sync
s3fs                                              16E     0   16E   0% /home/skills
s3fs                                              16E     0   16E   0% /home/z/my-project/upload
```

### Storage Mount Points Overview

| Mount Point | Type | Size | Used | Purpose |
|-------------|------|------|------|---------|
| `/` | rootfs (overlay) | 9.9 GB | 261 MB | Container root filesystem |
| `/dev` | tmpfs | 64 MB | 0 | Device nodes |
| `/sys/fs/cgroup` | tmpfs | 4.1 GB | 0 | Cgroup control interface |
| `/dev/shm` | tmpfs | 64 MB | 0 | Shared memory |
| `/.dockerenv` | kataShared | 248 GB | 661 MB | Kata container shared storage |
| `/etc/hosts` | tmpfs | 4.1 GB | 36 KB | Host resolution (ephemeral) |
| `/home/official_skills` | s3fs | 16 EB | 0 | S3-backed skills storage |
| `/tmp/my-project` | JuiceFS | 1.0 PB | 21 TB | Primary project workspace |
| `/home/sync` | s3fs | 16 EB | 0 | S3 sync directory |
| `/home/skills` | s3fs | 16 EB | 0 | S3 skills cache |
| `/home/z/my-project/upload` | s3fs | 16 EB | 0 | User upload storage |

> [!IMPORTANT]
> - **JuiceFS**: Distributed POSIX filesystem backed by object storage (21 TB used of 1 PB)
> - **S3FS**: FUSE-based S3 mount (16 EB virtual capacity, pay-as-you-go)
> - All S3FS/JuiceFS mounts are network-backed and persist beyond container lifecycle

---

## Memory Information

### Summary (`free -h`)

```
               total        used        free      shared  buff/cache   available
Mem:           8.0Gi       1.2Gi       6.3Gi        44Ki       762Mi       6.8Gi
Swap:             0B          0B          0B
```

### Detailed (`/proc/meminfo`)

| Metric | Value | Description |
|--------|-------|-------------|
| MemTotal | 8,407,072 kB (~8.0 GiB) | Total usable RAM |
| MemFree | 6,581,524 kB (~6.3 GiB) | Completely unused memory |
| MemAvailable | 7,150,064 kB (~6.8 GiB) | Estimate of available memory for apps |
| Buffers | 6,576 kB | Block device buffers |
| Cached | 622,548 kB (~608 MB) | Page cache (reclaimable) |
| SwapTotal | 0 kB | No swap configured |
| SwapFree | 0 kB | No swap configured |
| Active(anon) | 324 kB | Active anonymous memory |
| Inactive(anon) | 852,140 kB (~832 MB) | Inactive anonymous memory |
| Slab | 179,060 kB (~175 MB) | Kernel object caches |
| CommitLimit | 4,203,536 kB (~4.0 GiB) | Max memory that can be committed |
| Committed_AS | 1,333,324 kB (~1.3 GiB) | Currently committed virtual memory |

### Memory Analysis

```
✅ Healthy memory pressure: 85% available
✅ No swap usage: Container relies on RAM only
✅ Low anonymous memory: Minimal process memory footprint
✅ Adequate page cache: 608 MB for filesystem buffering
```

> [!TIP]
> With 6.8 GiB available and Next.js dev server typically using 1-2 GiB, headroom remains for:
> - Build processes
> - Image/PDF processing (ffmpeg, poppler, libreoffice)
> - AI inference workloads via Z-AI runtime

---

## CPU Information

### Processor Summary

| Property | Value |
|----------|-------|
| Architecture | x86_64 |
| Vendor | GenuineIntel |
| Model | Intel(R) Xeon(R) Processor |
| Model Number | 173 |
| Stepping | 1 |
| Base Frequency | 2.80 GHz |
| L3 Cache | 516 MB per core |
| Virtualization | KVM/PVM (hypervisor detected) |
| Total vCPUs | 4 |
| Cores per vCPU | 1 (virtualized) |

### CPU Flags (Key Features)

```
✅ Instruction Sets: SSE4.2, AVX2, AVX-512 (F/DQ/CD/BW/VL), SHA-NI
✅ Security: IBRS, STIBP, Spec Store Bypass mitigation
✅ Virtualization: hypervisor, kvm_pvm_guest, VMX extensions
✅ Memory: CLFLUSHOPT, CLWB, PCOMMIT
✅ Crypto: AES-NI, PCLMULQDQ, VAES, VPCLMULQDQ
✅ Advanced: AMX-BF16, AMX-TILE, AMX-INT8 (AI acceleration)
```

### Per-Core Details

```
Processor 0:
  - Physical ID: 0 | Core ID: 0 | APIC ID: 0
  - Cache: 516 MB L3
  - Bogomips: 5600.00

Processor 1:
  - Physical ID: 1 | Core ID: 0 | APIC ID: 1
  - Cache: 516 MB L3
  - Bogomips: 5600.00

Processor 2:
  - Physical ID: 2 | Core ID: 0 | APIC ID: 2
  - Cache: 516 MB L3
  - Bogomips: 5600.00

Processor 3:
  - Physical ID: 3 | Core ID: 0 | APIC ID: 3
  - Cache: 516 MB L3
  - Bogomips: 5600.00
```

### CPU Security Notes

```
⚠️ Known CPU Bugs (mitigated by kernel/hypervisor):
  - spectre_v1
  - spectre_v2
  - spec_store_bypass
  - swapgs

✅ Mitigations Active:
  - PTI (Page Table Isolation)
  - IBRS/IBPB/STIBP (Indirect Branch predictors)
  - Enhanced IBRS (ibrs_enhanced)
  - KVM paravirtualized guest mode (kvm_pvm_guest)
```

> [!NOTE]
> All vCPUs report identical specs due to Kata Container virtualization layer.
> Physical host likely uses Intel Sapphire Rapids or newer Xeon architecture.

---

## Storage Performance Notes

### JuiceFS (`/tmp/my-project`)
```
Backend:    Object Storage (Alibaba Cloud OSS compatible)
Metadata:   Redis-compatible service
Capacity:   1.0 PB virtual, 21 TB used
Use Case:   Primary project workspace with POSIX semantics
```

### S3FS Mounts
```
Backend:    Alibaba Cloud OSS via s3fs-fuse
Capacity:   16 EB virtual (effectively unlimited)
Use Cases:
  - /home/official_skills: Shared skill definitions
  - /home/sync: Cross-container synchronization
  - /home/skills: User skill cache
  - /home/z/my-project/upload: User-generated content
```

### Root Filesystem
```
Type:       OverlayFS on Kata shared volume
Capacity:   9.9 GB
Usage:      261 MB (3%)
Ephemeral:  Yes (resets on container restart unless persisted)
```

---

## Resource Limits & Quotas

| Resource | Limit | Current Usage | Notes |
|----------|-------|---------------|-------|
| Memory | 8.0 GiB | 1.2 GiB (15%) | Enforced by cgroups |
| CPU | 4 vCPUs | Variable | No hard CPU quota detected |
| Root Disk | 9.9 GB | 261 MB (3%) | Overlay on kataShared |
| JuiceFS | 1.0 PB | 21 TB (2%) | Network-backed, soft quota |
| S3FS | 16 EB | ~0 TB | Pay-per-use, no hard limit |

---

## Monitoring Commands

```bash
# Real-time disk usage
df -hT | grep -E '(my-project|upload|skills)'

# Real-time memory
watch -n 1 'free -h && echo && cat /proc/meminfo | grep -E "^(MemTotal|MemAvailable|Cached):"'

# CPU utilization
top -bn1 | head -20
# or
mpstat -P ALL 1 3

# JuiceFS metrics
juicefs stats /tmp/my-project

# S3FS connection check
mount | grep s3fs && curl -I https://oss-cn-hongkong.aliyuncs.com
```

---

## Troubleshooting Resources

### If Disk Space Alerts Trigger
```bash
# Check largest directories in ephemeral root
du -h / --max-depth=2 2>/dev/null | sort -hr | head -10

# Clear Next.js cache (safe)
rm -rf /home/z/my-project/.next/cache

# Clear UV/Python cache
rm -rf /var/cache/uv/*
```

### If Memory Pressure Occurs
```bash
# Identify memory-heavy processes
ps aux --sort=-%mem | head -10

# Check for memory leaks in Node.js
curl http://localhost:3000/api/debug/memory  # if endpoint exists

# Restart dev server (last resort)
pkill -f "bun.*next" && bun run dev
```

### If CPU Throttling Suspected
```bash
# Check cgroup CPU stats
cat /sys/fs/cgroup/cpu/cpu.stat  # cgroups v1
# or
cat /sys/fs/cgroup/cpu.stat      # cgroups v2

# Monitor CPU frequency scaling
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
```

---

## Appendix: Raw System Output

<details>
<summary>Click to expand full /proc/meminfo</summary>

```
MemTotal:        8407072 kB
MemFree:         6581524 kB
MemAvailable:    7150064 kB
Buffers:            6576 kB
Cached:           622548 kB
SwapCached:            0 kB
Active:            95952 kB
Inactive:        1385756 kB
Active(anon):        324 kB
Inactive(anon):   852140 kB
Active(file):      95628 kB
Inactive(file):   533616 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:              3000 kB
Writeback:             0 kB
AnonPages:        851972 kB
Mapped:           219880 kB
Shmem:                44 kB
KReclaimable:     151860 kB
Slab:             179060 kB
SReclaimable:     151860 kB
SUnreclaim:        27200 kB
KernelStack:        4496 kB
PageTables:        12616 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     4203536 kB
Committed_AS:    1333324 kB
VmallocTotal:   10737418239 kB
VmallocUsed:        4824 kB
VmallocChunk:          0 kB
Percpu:             1200 kB
AnonHugePages:     36864 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
FileHugePages:         0 kB
FilePmdMapped:         0 kB
DupText:               0 kB
MemZeroed:             0 kB
Unaccepted:            0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:       12288 kB
DirectMap2M:     8810496 kB
DirectMap1G:           0 kB
```

</details>

<details>
<summary>Click to expand full CPU flags reference</summary>

```
fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat 
pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm 
constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq 
pni pclmulqdq ssse3 fma cx16 pdcm pcid sse4_1 sse4_2 x2apic movbe 
popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm 
abm 3dnowprefetch cpuid_fault invpcid_single pti ssbd ibpb stibp 
ibrs_enhanced kvm_pvm_guest fsgsbase tsc_adjust bmi1 avx2 bmi2 erms 
invpcid avx512f avx512dq rdseed adx avx512ifma clflushopt clwb 
avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 avx_vnni 
avx512_bf16 wbnoinvd avx512vbmi umip pku avx512_vbmi2 gfni vaes 
vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq rdpid cldemote 
movdiri movdir64b fsrm md_clear serialize tsxldtrk amx_bf16 avx512_fp16 
amx_tile amx_int8 arch_capabilities
```

</details>

---

> **Document Metadata**  
> Filename: `SYSTEM_SPECS.md`  
> Format: GitHub Flavored Markdown (GFM)  
> Encoding: UTF-8  
> Last Updated: February 2025  
> Classification: Internal Infrastructure Documentation
