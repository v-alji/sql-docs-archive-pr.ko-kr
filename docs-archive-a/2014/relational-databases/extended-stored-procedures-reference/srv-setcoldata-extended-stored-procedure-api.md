---
title: srv_setcoldata(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: b67aa2f7b5a37057d2ed87846689919d84ec4aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739987"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a><span data-ttu-id="6aeaa-102">srv_setcoldata(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="6aeaa-102">srv_setcoldata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="6aeaa-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6aeaa-104">열 데이터의 현재 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-104">Specifies the current address for a column's data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aeaa-105">구문</span><span class="sxs-lookup"><span data-stu-id="6aeaa-105">Syntax</span></span>  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6aeaa-106">인수</span><span class="sxs-lookup"><span data-stu-id="6aeaa-106">Arguments</span></span>  
 <span data-ttu-id="6aeaa-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="6aeaa-107">*srvproc*</span></span>  
 <span data-ttu-id="6aeaa-108">특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="6aeaa-109">이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="6aeaa-110">*column*</span><span class="sxs-lookup"><span data-stu-id="6aeaa-110">*column*</span></span>  
 <span data-ttu-id="6aeaa-111">주소가 지정되는 열의 번호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-111">Indicates the number of the column the address is being specified for.</span></span> <span data-ttu-id="6aeaa-112">열 번호는 1부터 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="6aeaa-113">*data*</span><span class="sxs-lookup"><span data-stu-id="6aeaa-113">*data*</span></span>  
 <span data-ttu-id="6aeaa-114">열 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-114">Is a pointer for a column's data.</span></span> <span data-ttu-id="6aeaa-115">**srv_setcoldata**에 대한 다른 호출에 의해 열 데이터가 바뀌거나 **srv_senddone**이 호출될 때까지 *data*에 할당된 메모리를 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-115">Memory allocated for *data* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6aeaa-116">반환</span><span class="sxs-lookup"><span data-stu-id="6aeaa-116">Returns</span></span>  
 <span data-ttu-id="6aeaa-117">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="6aeaa-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aeaa-118">설명</span><span class="sxs-lookup"><span data-stu-id="6aeaa-118">Remarks</span></span>  
 <span data-ttu-id="6aeaa-119">먼저 **srv_describe**를 사용하여 행의 각 열을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-119">Each column of the row must be defined first with **srv_describe**.</span></span> <span data-ttu-id="6aeaa-120">열 데이터 주소는 처음에 **srv_describe**를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-120">Column data addresses are initially set with **srv_describe**.</span></span> <span data-ttu-id="6aeaa-121">열 데이터의 주소가 변경되면 **srv_setcoldata**를 호출하여 데이터의 새 주소를 지정해야 하며, 변경된 각 열에 대해 개별적으로 **srv_setcoldata**를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-121">If the address of the column data changes, **srv_setcoldata** must be called to specify the new address of the data and **srv_setcoldata** must be called separately for each changed column.</span></span>  
  
 <span data-ttu-id="6aeaa-122">**srv_setcollen**을 사용하여 열의 길이를 0으로 설정하면 Null 데이터가 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-122">Null data is represented by setting the column's length to 0 with **srv_setcollen**.</span></span> <span data-ttu-id="6aeaa-123">데이터 주소는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-123">The data address is then ignored.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6aeaa-124">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6aeaa-125">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6aeaa-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aeaa-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6aeaa-126">See Also</span></span>  
 [<span data-ttu-id="6aeaa-127">srv_describe &#40;확장 저장 프로시저 API&#41;</span><span class="sxs-lookup"><span data-stu-id="6aeaa-127">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
