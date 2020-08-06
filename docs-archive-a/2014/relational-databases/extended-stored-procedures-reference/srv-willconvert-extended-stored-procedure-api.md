---
title: srv_willconvert(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_willconvert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b9adfbd2a73b30cbfc0229b7942f79d3ddc1a82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742112"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a><span data-ttu-id="329ea-102">srv_willconvert(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="329ea-102">srv_willconvert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="329ea-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="329ea-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="329ea-104">ODS 라이브러리 내에서 특정 데이터 형식 변환이 가능한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-104">Determines whether a specific data type conversion is available within the ODS Library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329ea-105">구문</span><span class="sxs-lookup"><span data-stu-id="329ea-105">Syntax</span></span>  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="329ea-106">인수</span><span class="sxs-lookup"><span data-stu-id="329ea-106">Arguments</span></span>  
 <span data-ttu-id="329ea-107">*srctype*</span><span class="sxs-lookup"><span data-stu-id="329ea-107">*srctype*</span></span>  
 <span data-ttu-id="329ea-108">변환할 데이터의 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-108">Indicates the data type of the data to be converted.</span></span> <span data-ttu-id="329ea-109">이 매개 변수는 임의의 확장 저장 프로시저 API 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-109">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
 <span data-ttu-id="329ea-110">*desttype*</span><span class="sxs-lookup"><span data-stu-id="329ea-110">*desttype*</span></span>  
 <span data-ttu-id="329ea-111">원본 데이터를 변환할 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-111">Indicates the data type to which the source data is converted.</span></span> <span data-ttu-id="329ea-112">이 매개 변수는 임의의 확장 저장 프로시저 API 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-112">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="329ea-113">반환</span><span class="sxs-lookup"><span data-stu-id="329ea-113">Returns</span></span>  
 <span data-ttu-id="329ea-114">데이터 형식 변환이 지원되면 True, 데이터 형식 변환이 지원되지 않으면 False입니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-114">TRUE if the data type conversion is supported; FALSE if the data type conversion is not supported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="329ea-115">설명</span><span class="sxs-lookup"><span data-stu-id="329ea-115">Remarks</span></span>  
 <span data-ttu-id="329ea-116">각 데이터 형식에 대한 설명은 [데이터 형식(확장 저장 프로시저 API)](data-types-extended-stored-procedure-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="329ea-116">For a description of each data type, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="329ea-117">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="329ea-117">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="329ea-118">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="329ea-118">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329ea-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="329ea-119">See Also</span></span>  
 [<span data-ttu-id="329ea-120">srv_convert(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="329ea-120">srv_convert &#40;Extended Stored Procedure API&#41;</span></span>](srv-convert-extended-stored-procedure-api.md)  
  
  
