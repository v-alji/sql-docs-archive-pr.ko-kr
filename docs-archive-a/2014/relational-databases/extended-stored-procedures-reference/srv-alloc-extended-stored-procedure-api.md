---
title: srv_alloc(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b372c1b43987e5bebd1fb82e995dc6d262455ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648393"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a><span data-ttu-id="64077-102">srv_alloc(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="64077-102">srv_alloc (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="64077-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="64077-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="64077-104">메모리를 동적으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="64077-104">Allocates memory dynamically.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64077-105">구문</span><span class="sxs-lookup"><span data-stu-id="64077-105">Syntax</span></span>  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="64077-106">인수</span><span class="sxs-lookup"><span data-stu-id="64077-106">Arguments</span></span>  
 <span data-ttu-id="64077-107">*size*</span><span class="sxs-lookup"><span data-stu-id="64077-107">*size*</span></span>  
 <span data-ttu-id="64077-108">할당할 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64077-108">Specifies the number of bytes to allocate.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="64077-109">반환</span><span class="sxs-lookup"><span data-stu-id="64077-109">Returns</span></span>  
 <span data-ttu-id="64077-110">새로 할당된 공간을 가리키는 포인터.</span><span class="sxs-lookup"><span data-stu-id="64077-110">A pointer to the newly allocated space.</span></span> <span data-ttu-id="64077-111">*size*바이트를 할당할 수 없는 경우 null 포인터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="64077-111">If *size* bytes cannot be allocated, a null pointer is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64077-112">설명</span><span class="sxs-lookup"><span data-stu-id="64077-112">Remarks</span></span>  
 <span data-ttu-id="64077-113">**srv_alloc** 함수는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API **GlobalAlloc** 함수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="64077-113">The **srv_alloc** function is equivalent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API  **GlobalAlloc** function.</span></span> <span data-ttu-id="64077-114">일반적인 Windows API C 런타임 메모리 관리 함수는 확장 저장 프로시저 API 애플리케이션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64077-114">Normal Windows API C run-time memory management functions can be used in an Extended Stored Procedure API application.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64077-115">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64077-115">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="64077-116">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="64077-116">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
