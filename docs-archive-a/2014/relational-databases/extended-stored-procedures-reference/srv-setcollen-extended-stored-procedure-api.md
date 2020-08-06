---
title: srv_setcollen(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcollen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e3023e2ac239e074656329da7d8af3aba3afa88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730684"
---
# <a name="srv_setcollen-extended-stored-procedure-api"></a><span data-ttu-id="7b559-102">srv_setcollen(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="7b559-102">srv_setcollen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="7b559-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="7b559-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="7b559-104">가변 길이 열이나 NULL 값을 허용하는 열의 현재 데이터 길이(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-104">Specifies the current data length in bytes of a variable-length column or a column that allows NULL values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b559-105">구문</span><span class="sxs-lookup"><span data-stu-id="7b559-105">Syntax</span></span>  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b559-106">인수</span><span class="sxs-lookup"><span data-stu-id="7b559-106">Arguments</span></span>  
 <span data-ttu-id="7b559-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="7b559-107">*srvproc*</span></span>  
 <span data-ttu-id="7b559-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="7b559-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="7b559-110">*column*</span><span class="sxs-lookup"><span data-stu-id="7b559-110">*column*</span></span>  
 <span data-ttu-id="7b559-111">데이터 길이가 지정되는 열의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-111">Indicates the number of the column for which the data length is being specified.</span></span> <span data-ttu-id="7b559-112">열 번호는 1부터 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="7b559-113">*길이가*</span><span class="sxs-lookup"><span data-stu-id="7b559-113">*len*</span></span>  
 <span data-ttu-id="7b559-114">열 데이터의 길이(바이트)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-114">Indicates the length, in bytes, of the column data.</span></span> <span data-ttu-id="7b559-115">길이가 0이면 열 데이터 값이 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-115">A length of 0 means the column data value is null.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7b559-116">반환</span><span class="sxs-lookup"><span data-stu-id="7b559-116">Returns</span></span>  
 <span data-ttu-id="7b559-117">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="7b559-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b559-118">설명</span><span class="sxs-lookup"><span data-stu-id="7b559-118">Remarks</span></span>  
 <span data-ttu-id="7b559-119">먼저 **srv_describe**를 사용하여 행의 각 열을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-119">Each column of the row must first be defined with **srv_describe**.</span></span> <span data-ttu-id="7b559-120">열 데이터 길이는 **srv_describe** 또는 **srv_setcollen**에 대한 마지막 호출에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-120">The column data length is set by the last call to **srv_describe** or **srv_setcollen**.</span></span> <span data-ttu-id="7b559-121">행의 가변 길이 데이터(Null로 끝나는 데이터)가 변경되는 경우 **srv_sendrow**를 호출하기 전에 **srv_setcollen**을 사용하여 새 길이로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-121">If variable-length data (null-terminated data) changes for a row, **srv_setcollen** must be used to set it to the new length before calling **srv_sendrow**.</span></span> <span data-ttu-id="7b559-122">Null 값을 허용하는 열의 경우 *desttype*이 Null을 허용하는 데이터 형식(예: SRVINTN)으로 설정되어 **srv_describe**가 호출되었으며, *len*을 0으로 설정하여 **srv_setcollen**이 호출되어 Null 데이터가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-122">For a column that allows null values, **srv_describe** must have been called with *desttype* set to a data type that allows nulls (like SRVINTN) and null data is specified by calling **srv_setcollen** with *len* set to 0.</span></span> <span data-ttu-id="7b559-123">길이가 0인 데이터는 확장 저장 프로시저 API를 사용하여 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-123">Zero length data cannot be specified using the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="7b559-124">열의 데이터 형식이 가변 길이인 경우에는 *len*이 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-124">Note that when the data type of the column is variable-length, *len* is not checked.</span></span> <span data-ttu-id="7b559-125">고정 길이 열에 대해 호출하면 이 함수는 FAIL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-125">This function returns FAIL if called for a fixed-length column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b559-126">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b559-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="7b559-127">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b559-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b559-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b559-128">See Also</span></span>  
 [<span data-ttu-id="7b559-129">srv_describe &#40;확장 저장 프로시저 API&#41;</span><span class="sxs-lookup"><span data-stu-id="7b559-129">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
