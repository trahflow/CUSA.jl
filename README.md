# Demo showing weird interaction between CUDA, StaticArrays and Test

### what works

```julia-repl
julia> using CUSA

julia> staticarrays()
(Float32[14.372921, -0.6995831, 6.592437], Float32[14.372921, -0.69958264, 6.5924377])
```

### what doesn't work

```julia-repl
(CUSA) pkg> test
     Testing CUSA

.
.
.

CUDA + Staticarrays: Error During Test at /home/le58wel/Repos/CUSA/test/runtests.jl:4
  Got exception outside of a @test
  InvalidIRError: compiling MethodInstance for (::CUSA.var"#sa_kernel#2")(::Val{3}, ::CUDA.CuDeviceVector{Float32, 1}, ::CUDA.CuDeviceArray{Float32, 3, 1}, ::CUDA.CuDeviceMatrix{Float32, 1}, ::StaticArraysCore.SVector{3, Float32}) resulted in invalid LLVM IR
  Reason: unsupported call to an unknown function (call to julia.new_gc_frame)
  Reason: unsupported call to an unknown function (call to julia.push_gc_frame)
  Reason: unsupported call to an unknown function (call to julia.get_gc_frame_slot)
  Reason: unsupported dynamic function invocation (call to dimension_mismatch_fail(SA::Type, a::AbstractArray) @ StaticArrays ~/julia-depots/gpu/packages/StaticArrays/oOCPP/src/convert.jl:195)

```