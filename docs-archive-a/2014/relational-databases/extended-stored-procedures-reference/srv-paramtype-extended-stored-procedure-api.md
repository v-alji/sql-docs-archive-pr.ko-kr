---
title: srv_paramtype(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4b4006f8214670e3bd2bddfbaabe917fb9d778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648389"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a><span data-ttu-id="15d09-102">srv_paramtype(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="15d09-102">srv_paramtype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="15d09-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="15d09-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="15d09-104">원격 저장 프로시저 호출 매개 변수의 데이터 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-104">Returns the data type of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d09-105">구문</span><span class="sxs-lookup"><span data-stu-id="15d09-105">Syntax</span></span>  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="15d09-106">인수</span><span class="sxs-lookup"><span data-stu-id="15d09-106">Arguments</span></span>  
 <span data-ttu-id="15d09-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="15d09-107">*srvproc*</span></span>  
 <span data-ttu-id="15d09-108">특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="15d09-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="15d09-110">*n*</span><span class="sxs-lookup"><span data-stu-id="15d09-110">*n*</span></span>  
 <span data-ttu-id="15d09-111">매개 변수의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="15d09-112">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-112">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="15d09-113">반환</span><span class="sxs-lookup"><span data-stu-id="15d09-113">Returns</span></span>  
 <span data-ttu-id="15d09-114">매개 변수의 데이터 형식에 대한 토큰 값입니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-114">A token value for the data type of the parameter.</span></span> <span data-ttu-id="15d09-115">데이터 형식에 대한 자세한 내용은 [데이터 형식(확장 저장 프로시저 API)](data-types-extended-stored-procedure-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15d09-115">For information about data types, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="15d09-116">*n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 -1이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns - 1.</span></span>  
  
 <span data-ttu-id="15d09-117">매개 변수가 데이터 형식 중 하나인 경우이 함수는 다음 값을 반환 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="15d09-117">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="15d09-118">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="15d09-118">New data types</span></span>|<span data-ttu-id="15d09-119">반환 값</span><span class="sxs-lookup"><span data-stu-id="15d09-119">Return value</span></span>|  
|--------------------|------------------|  
|`BITN`|<span data-ttu-id="15d09-120">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="15d09-120">SRVBIT</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="15d09-121">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="15d09-121">VARCHAR</span></span>|  
|`BIGCHAR`|<span data-ttu-id="15d09-122">CHAR</span><span class="sxs-lookup"><span data-stu-id="15d09-122">CHAR</span></span>|  
|`BIGBINARY`|<span data-ttu-id="15d09-123">BINARY</span><span class="sxs-lookup"><span data-stu-id="15d09-123">BINARY</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="15d09-124">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="15d09-124">VARBINARY</span></span>|  
|`NCHAR`|<span data-ttu-id="15d09-125">CHAR</span><span class="sxs-lookup"><span data-stu-id="15d09-125">CHAR</span></span>|  
|`NVARCHAR`|<span data-ttu-id="15d09-126">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="15d09-126">VARCHAR</span></span>|  
|`NTEXT`|<span data-ttu-id="15d09-127">-1</span><span class="sxs-lookup"><span data-stu-id="15d09-127">-1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15d09-128">설명</span><span class="sxs-lookup"><span data-stu-id="15d09-128">Remarks</span></span>  
 <span data-ttu-id="15d09-129">매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-129">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="15d09-130">일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-130">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="15d09-131">SRV_RPC 처리기는 계속 호출 되지만 매개 변수가 없고 **srv_rpcparams** 0을 반환 하는 것 처럼 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-131">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="15d09-132">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d09-132">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="15d09-133">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15d09-133">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d09-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15d09-134">See Also</span></span>  
 <span data-ttu-id="15d09-135">[srv_paraminfo &#40;확장 저장 프로시저 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="15d09-135">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="15d09-136">srv_rpcparams(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="15d09-136">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
