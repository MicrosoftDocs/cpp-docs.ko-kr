---
description: '자세히 알아보기: Concurrency:: graphics 네임 스페이스 함수'
title: Concurrency::graphics 네임스페이스 함수
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::fast_math::copy_async
- amp_graphics/Concurrency::fast_math::copy
ms.assetid: ace01cd5-29d3-4356-930e-c81a61c5f934
ms.openlocfilehash: dab12e4a0d1c767d9422991679ed59152cd89c1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122280"
---
# <a name="concurrencygraphics-namespace-functions"></a>Concurrency::graphics 네임스페이스 함수

[복사](#copy)\
[copy_async](#copy_async)

## <a name="copy-function-concurrencygraphics-namespace"></a><a name="copy"></a> copy 함수 (Concurrency:: graphics 네임 스페이스)

소스 텍스처를 대상 버퍼에 복사 하거나 소스 버퍼를 대상 버퍼에 복사 합니다. 이 함수의 일반적인 형태는 `copy(src, dest)` 입니다.

```cpp
template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type>
>
void copy (
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size,
    _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>void copy(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent, OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture,
    void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>매개 변수

*_Copy_extent*<br/>
복사할 질감 섹션의 범위입니다.

*_Dst*<br/>
복사할 개체입니다.

*_Dst_byte_size*<br/>
대상의 바이트 수입니다.

*_Dst_type*<br/>
대상 개체의 형식입니다.

*_Dst_offset*<br/>
복사를 시작할 대상에 대 한 오프셋입니다.

*InputIterator*<br/>
입력 반복기의 형식입니다.

*OutputIterator*<br/>
출력 반복기의 형식입니다.

*_Src*<br/>
복사할 개체입니다.

*_Src_byte_size*<br/>
소스의 바이트 수입니다.

*_Src_type*<br/>
원본 개체의 형식입니다.

*_Src_offset*<br/>
원본에서 복사를 시작할 오프셋입니다.

*first*<br/>
소스 컨테이너에 대 한 시작 반복기입니다.

*last*<br/>
소스 컨테이너에 대 한 종료 반복기입니다.

## <a name="copy_async-function-concurrencygraphics-namespace"></a><a name="copy_async"></a> copy_async 함수 (Concurrency:: graphics 네임 스페이스)

소스 텍스처를 대상 버퍼에 비동기적으로 복사 하거나 소스 버퍼를 대상 버퍼에 복사한 다음 대기 시킬 수 있는 [completion_future](completion-future-class.md) 개체를 반환 합니다. 코드가 액셀러레이터 키에서 실행 중일 때는 데이터를 복사할 수 없습니다. 이 함수의 일반적인 형태는 `copy(src, dest)` 입니다.

```cpp
template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type &_Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>매개 변수

*_Copy_extent*<br/>
복사할 질감 섹션의 범위입니다.

*_Dst*<br/>
복사할 개체입니다.

*_Dst_byte_size*<br/>
대상의 바이트 수입니다.

*_Dst_type*<br/>
대상 개체의 형식입니다.

*_Dst_offset*<br/>
복사를 시작할 대상에 대 한 오프셋입니다.

*InputIterator*<br/>
입력 반복기의 형식입니다.

*OutputIterator*<br/>
출력 반복기의 형식입니다.

*_Src*<br/>
복사할 개체입니다.

*_Src_byte_size*<br/>
소스의 바이트 수입니다.

*_Src_type*<br/>
원본 개체의 형식입니다.

*_Src_offset*<br/>
원본에서 복사를 시작할 오프셋입니다.

*first*<br/>
소스 컨테이너에 대 한 시작 반복기입니다.

*last*<br/>
소스 컨테이너에 대 한 종료 반복기입니다.

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics. h

**네임 스페이스:** Concurrency:: graphics

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)
