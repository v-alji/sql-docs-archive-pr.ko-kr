---
title: srv_pfieldex(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: a474eafcb6b6d42161a7e67ce7f93636269c46c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648388"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a><span data-ttu-id="9203d-102">srv_pfieldex(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="9203d-102">srv_pfieldex (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="9203d-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9203d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="9203d-104">요청한 SRV_PROC 필드가 포함된 데이터에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-104">Returns a pointer to data containing the requested SRV_PROC field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9203d-105">구문</span><span class="sxs-lookup"><span data-stu-id="9203d-105">Syntax</span></span>  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="9203d-106">인수</span><span class="sxs-lookup"><span data-stu-id="9203d-106">Arguments</span></span>  
 <span data-ttu-id="9203d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="9203d-107">*srvproc*</span></span>  
 <span data-ttu-id="9203d-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="9203d-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="9203d-110">*필드가*</span><span class="sxs-lookup"><span data-stu-id="9203d-110">*field*</span></span>  
 <span data-ttu-id="9203d-111">반환할 *srvproc* 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-111">Specifies the *srvproc* field to return.</span></span>  
  
|<span data-ttu-id="9203d-112">필드</span><span class="sxs-lookup"><span data-stu-id="9203d-112">Field</span></span>|<span data-ttu-id="9203d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9203d-113">Description</span></span>|<span data-ttu-id="9203d-114">반환 형식</span><span class="sxs-lookup"><span data-stu-id="9203d-114">Return-type</span></span>|  
|-----------|-----------------|------------------|  
|<span data-ttu-id="9203d-115">SRV_MSGLCID</span><span class="sxs-lookup"><span data-stu-id="9203d-115">SRV_MSGLCID</span></span>|<span data-ttu-id="9203d-116">현재 세션 메시지 LCID입니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-116">Current session message LCID.</span></span>|<span data-ttu-id="9203d-117">ULONG\*</span><span class="sxs-lookup"><span data-stu-id="9203d-117">ULONG\*</span></span>|  
|<span data-ttu-id="9203d-118">SRV_INSTANCENAME</span><span class="sxs-lookup"><span data-stu-id="9203d-118">SRV_INSTANCENAME</span></span>|<span data-ttu-id="9203d-119">인스턴스 이름(명명된 경우)을 반환하거나, 그렇지 않으면 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-119">Instance name (if named); otherwise, returns NULL.</span></span>|<span data-ttu-id="9203d-120">WCHAR\*</span><span class="sxs-lookup"><span data-stu-id="9203d-120">WCHAR\*</span></span>|  
  
 <span data-ttu-id="9203d-121">*길이가*</span><span class="sxs-lookup"><span data-stu-id="9203d-121">*len*</span></span>  
 <span data-ttu-id="9203d-122">반환된 *field* 값의 길이(바이트)가 포함된 **int** 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-122">Is a pointer to an **int** variable that contains the length of the returned *field* value in bytes.</span></span> <span data-ttu-id="9203d-123">*len*이 NULL이면 길이가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-123">If *len* is NULL, the length is not returned.</span></span> <span data-ttu-id="9203d-124">NULL이 반환되면 \**len*이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-124">When NULL is returned \**len* is set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="9203d-125">반환</span><span class="sxs-lookup"><span data-stu-id="9203d-125">Returns</span></span>  
 <span data-ttu-id="9203d-126">*field*에 따라 형식이 결정되는 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-126">A pointer to data whose type depends on *field*.</span></span> <span data-ttu-id="9203d-127">*len*이 NULL이거나 *srvproc*가 NULL이면 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-127">NULL is returned when *len* is NULL or *srvproc* is NULL.</span></span> <span data-ttu-id="9203d-128">*field*를 알 수 없으면 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-128">If the *field* is unknown, NULL is returned.</span></span> <span data-ttu-id="9203d-129">NULL이 반환되면 \**len*이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-129">When NULL is returned \**len* is set to 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9203d-130">서버에서 반환되는 버퍼는 읽기 전용이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-130">The buffer returned from the server should be read only.</span></span> <span data-ttu-id="9203d-131">그렇지 않으면 서버 상태가 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-131">Otherwise, the server state may be corrupted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9203d-132">설명</span><span class="sxs-lookup"><span data-stu-id="9203d-132">Remarks</span></span>  
 <span data-ttu-id="9203d-133">**보안 정보** 확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 컴파일한 DLL을 설치하기 전에 해당 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9203d-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="9203d-134">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9203d-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
