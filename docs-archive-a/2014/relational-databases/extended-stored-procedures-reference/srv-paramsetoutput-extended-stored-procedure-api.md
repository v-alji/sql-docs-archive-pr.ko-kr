---
title: srv_paramsetoutput(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 2847367fe5d6052728cebf30467b68cb14fb8e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647011"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a><span data-ttu-id="0a841-102">srv_paramsetoutput(확장 저장 프로시저 API)</span><span class="sxs-lookup"><span data-stu-id="0a841-102">srv_paramsetoutput (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0a841-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0a841-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="0a841-104">반환 매개 변수의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-104">Sets the value of a return parameter.</span></span> <span data-ttu-id="0a841-105">이 함수는 **srv_paramset** 함수를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-105">This function supersedes the **srv_paramset** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a841-106">구문</span><span class="sxs-lookup"><span data-stu-id="0a841-106">Syntax</span></span>  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a841-107">인수</span><span class="sxs-lookup"><span data-stu-id="0a841-107">Arguments</span></span>  
 <span data-ttu-id="0a841-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="0a841-108">*srvproc*</span></span>  
 <span data-ttu-id="0a841-109">클라이언트 연결의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-109">Is a handle for a client connection.</span></span>  
  
 <span data-ttu-id="0a841-110">*n*</span><span class="sxs-lookup"><span data-stu-id="0a841-110">*n*</span></span>  
 <span data-ttu-id="0a841-111">설정할 매개 변수의 서수입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-111">Is the ordinal number of the parameter to be set.</span></span> <span data-ttu-id="0a841-112">첫 번째 매개 변수는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="0a841-113">*pbData*</span><span class="sxs-lookup"><span data-stu-id="0a841-113">*pbData*</span></span>  
 <span data-ttu-id="0a841-114">클라이언트에 프로시저 반환 매개 변수로 전달될 데이터 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-114">Is a pointer to the data value to be sent back to the client as a procedure return parameter.</span></span>  
  
 <span data-ttu-id="0a841-115">*cbLen*</span><span class="sxs-lookup"><span data-stu-id="0a841-115">*cbLen*</span></span>  
 <span data-ttu-id="0a841-116">반환할 데이터의 실제 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-116">Is the actual length of the data to be returned.</span></span> <span data-ttu-id="0a841-117">매개 변수의 데이터 형식이 상수 길이 값이고 Null 값을 허용하지 않는 경우(예: *srvbit* 또는 *srvint1*) *cbLen*은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-117">If the data type of the parameter specifies values of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *cbLen* is ignored.</span></span> <span data-ttu-id="0a841-118">*fNull*이 FALSE인 경우 값이 0이면 길이가 0인 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-118">A value of 0 signifies zero-length data if *fNull* is FALSE.</span></span>  
  
 <span data-ttu-id="0a841-119">*fNull*</span><span class="sxs-lookup"><span data-stu-id="0a841-119">*fNull*</span></span>  
 <span data-ttu-id="0a841-120">반환 매개 변수의 값이 NULL인지 여부를 나타내는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-120">Is a flag indicating whether the value of the return parameter is NULL.</span></span> <span data-ttu-id="0a841-121">매개 변수가 NULL로 설정되어야 하는 경우 이 플래그를 TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-121">Set this flag to TRUE if the parameter should be set to NULL.</span></span> <span data-ttu-id="0a841-122">기본값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-122">The default value is FALSE.</span></span> <span data-ttu-id="0a841-123">*fNull*이 TRUE로 설정되어 있는 경우 *cbLen*을 0으로 설정하지 않으면 함수가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-123">If *fNull* is set to TRUE, *cbLen* should be set to 0 or the function will fail.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0a841-124">반환</span><span class="sxs-lookup"><span data-stu-id="0a841-124">Returns</span></span>  
 <span data-ttu-id="0a841-125">매개 변수 정보가 성공적으로 설정되면 SUCCEED가 반환되고 그렇지 않으면 FAIL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-125">If the parameter information was successfully set, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="0a841-126">FAIL은 다음과 같은 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-126">FAIL is returned when</span></span>  
  
-   <span data-ttu-id="0a841-127">매개 변수가 반환 매개 변수가 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="0a841-127">the parameter is not a return parameter, or</span></span>  
  
-   <span data-ttu-id="0a841-128">*cbLen* 인수가 잘못된 경우</span><span class="sxs-lookup"><span data-stu-id="0a841-128">the *cbLen* argument is invalid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a841-129">설명</span><span class="sxs-lookup"><span data-stu-id="0a841-129">Remarks</span></span>  
 <span data-ttu-id="0a841-130">**보안 정보** 확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 컴파일한 DLL을 설치하기 전에 해당 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a841-130">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="0a841-131">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a841-131">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
