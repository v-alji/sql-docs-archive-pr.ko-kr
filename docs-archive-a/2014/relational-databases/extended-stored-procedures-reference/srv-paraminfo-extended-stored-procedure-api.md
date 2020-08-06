---
title: srv_paraminfo(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: cc3d51acc2ca560246c46267840db72934223999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742139"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a><span data-ttu-id="f20f6-102">srv_paraminfo(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="f20f6-102">srv_paraminfo (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="f20f6-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f20f6-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f20f6-104">매개 변수에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-104">Returns information about a parameter.</span></span> <span data-ttu-id="f20f6-105">이 함수는 [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) 및 [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md) 함수를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-105">This function supersedes the following functions: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md), and [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="f20f6-106">**srv_paraminfo**는 [데이터 형식](data-types-extended-stored-procedure-api.md)의 데이터 형식과 길이가 0인 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-106">**srv_paraminfo** supports the data types in [Data Types](data-types-extended-stored-procedure-api.md) and zero-length data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f20f6-107">구문</span><span class="sxs-lookup"><span data-stu-id="f20f6-107">Syntax</span></span>  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f20f6-108">인수</span><span class="sxs-lookup"><span data-stu-id="f20f6-108">Arguments</span></span>  
 <span data-ttu-id="f20f6-109">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="f20f6-109">*srvproc*</span></span>  
 <span data-ttu-id="f20f6-110">클라이언트 연결의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-110">A handle for a client connection.</span></span>  
  
 <span data-ttu-id="f20f6-111">*n*</span><span class="sxs-lookup"><span data-stu-id="f20f6-111">*n*</span></span>  
 <span data-ttu-id="f20f6-112">설정할 매개 변수의 서수입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-112">The ordinal number of the parameter to be set.</span></span> <span data-ttu-id="f20f6-113">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="f20f6-114">*pbType*</span><span class="sxs-lookup"><span data-stu-id="f20f6-114">*pbType*</span></span>  
 <span data-ttu-id="f20f6-115">매개 변수의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-115">The data type of the parameter.</span></span>  
  
 <span data-ttu-id="f20f6-116">*pcbMaxLen*</span><span class="sxs-lookup"><span data-stu-id="f20f6-116">*pcbMaxLen*</span></span>  
 <span data-ttu-id="f20f6-117">매개 변수의 최대 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-117">Pointer to the maximum length of the parameter.</span></span>  
  
 <span data-ttu-id="f20f6-118">*pcbActualLen*</span><span class="sxs-lookup"><span data-stu-id="f20f6-118">*pcbActualLen*</span></span>  
 <span data-ttu-id="f20f6-119">매개 변수의 실제 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-119">Pointer to the actual length of the parameter.</span></span> <span data-ttu-id="f20f6-120">\**pfNull*이 FALSE로 설정되어 있으면 0 값(\**pcbActualLen* == 0)은 길이가 0인 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-120">A value of 0 (\**pcbActualLen* == 0) signifies zero-length data if \**pfNull* is set to FALSE.</span></span>  
  
 <span data-ttu-id="f20f6-121">*pbData*</span><span class="sxs-lookup"><span data-stu-id="f20f6-121">*pbData*</span></span>  
 <span data-ttu-id="f20f6-122">매개 변수 데이터의 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-122">Pointer to the buffer for parameter data.</span></span> <span data-ttu-id="f20f6-123">*pbData*가 NULL이 아닌 경우 확장 저장 프로시저 API는 \**pcbActualLen* 바이트의 데이터를 \**pbData*에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-123">If *pbData* is not NULL, the Extended Store Procedure API writes \**pcbActualLen* bytes of data to \**pbData*.</span></span> <span data-ttu-id="f20f6-124">*pbData*가 NULL인 경우 데이터가 \**pbData*에 기록되지 않지만 함수는 \**pbType*, \**pcbMaxLen*, \**pcbActualLen* 및 \**pfNull*을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-124">If *pbData* is NULL, no data is written to \**pbData* but the function returns \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, and \**pfNull*.</span></span> <span data-ttu-id="f20f6-125">이 버퍼에 대한 메모리는 애플리케이션으로 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-125">The memory for this buffer must be managed by the application.</span></span>  
  
 <span data-ttu-id="f20f6-126">*pfNull*</span><span class="sxs-lookup"><span data-stu-id="f20f6-126">*pfNull*</span></span>  
 <span data-ttu-id="f20f6-127">NULL 플래그에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-127">Pointer to a null flag.</span></span><span data-ttu-id="f20f6-128">매개 변수 값이 NULL인 경우  \**pfNull*이 TRUE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-128">\ **pfNull* is set to TRUE if the value of the parameter is NULL.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f20f6-129">반환</span><span class="sxs-lookup"><span data-stu-id="f20f6-129">Returns</span></span>  
 <span data-ttu-id="f20f6-130">매개 변수 정보를 성공적으로 가져오면 SUCCEED가 반환되고 그렇지 않으면 FAIL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-130">If the parameter information was successfully obtained, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="f20f6-131">현재 원격 저장 프로시저가 없고 *n*번째 원격 저장 프로시저 매개 변수가 없으면 FAIL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-131">FAIL is returned when there is no current remote stored procedure and when there is no *n*th remote stored procedure parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f20f6-132">설명</span><span class="sxs-lookup"><span data-stu-id="f20f6-132">Remarks</span></span>  
 <span data-ttu-id="f20f6-133">**보안 정보** 확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 컴파일한 DLL을 설치하기 전에 해당 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20f6-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f20f6-134">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f20f6-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20f6-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f20f6-135">See Also</span></span>  
 [<span data-ttu-id="f20f6-136">확장 저장 프로시저 프로그래머 참조</span><span class="sxs-lookup"><span data-stu-id="f20f6-136">Extended Stored Procedures Programmer's Reference</span></span>](database-engine-extended-stored-procedures-reference.md)  
  
  
