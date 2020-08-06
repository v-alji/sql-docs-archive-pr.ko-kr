---
title: 확장 저장 프로시저 프로그래머 참조 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3b1beade751cd7a7407f3c33eb7f8ae58c9fd4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660580"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a><span data-ttu-id="ff394-102">확장 저장 프로시저 프로그래머&#39;s 참조</span><span class="sxs-lookup"><span data-stu-id="ff394-102">Extended Stored Procedures Programmer&#39;s Reference</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="ff394-103">대신 CLR 통합을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ff394-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ff394-104">이전에 개방형 Data Services의 일부였던 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 확장 저장 프로시저 API는 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 확장하기 위한 서버 기반 API(애플리케이션 프로그래밍 인터페이스)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ff394-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Extended Stored Procedure API, previously part of Open Data Services, provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="ff394-105">API는 애플리케이션을 빌드하는 데 사용되는 C 및 C++ 함수와 매크로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff394-105">The API consists of C and C++ functions and macros used to build applications.</span></span>  
  
 <span data-ttu-id="ff394-106">CLR 통합과 같은 보다 강력한 최신 기술이 등장하면서 확장 저장 프로시저의 필요성이 크게 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="ff394-106">With the emergence of newer and more powerful technologies such as CLR integration, the need for extended stored procedures has largely been replaced.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff394-107">확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff394-107">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ff394-108">보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff394-108">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff394-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ff394-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="ff394-110">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="ff394-110">Data Types</span></span>](srv-pfield-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-111">srv_alloc</span><span class="sxs-lookup"><span data-stu-id="ff394-111">srv_alloc</span></span>](srv-alloc-extended-stored-procedure-api.md)||  
|[<span data-ttu-id="ff394-112">srv_convert</span><span class="sxs-lookup"><span data-stu-id="ff394-112">srv_convert</span></span>](srv-pfieldex-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-113">srv_describe</span><span class="sxs-lookup"><span data-stu-id="ff394-113">srv_describe</span></span>](srv-rpcdb-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-114">srv_getbindtoken</span><span class="sxs-lookup"><span data-stu-id="ff394-114">srv_getbindtoken</span></span>](srv-rpcname-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-115">srv_got_attention</span><span class="sxs-lookup"><span data-stu-id="ff394-115">srv_got_attention</span></span>](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[<span data-ttu-id="ff394-116">srv_rpcoptions</span><span class="sxs-lookup"><span data-stu-id="ff394-116">srv_rpcoptions</span></span>](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-117">srv_message_handler</span><span class="sxs-lookup"><span data-stu-id="ff394-117">srv_message_handler</span></span>](srv-rpcowner-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-118">srv_paramdata</span><span class="sxs-lookup"><span data-stu-id="ff394-118">srv_paramdata</span></span>](srv-rpcparams-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-119">srv_paraminfo</span><span class="sxs-lookup"><span data-stu-id="ff394-119">srv_paraminfo</span></span>](srv-senddone-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-120">srv_paramlen</span><span class="sxs-lookup"><span data-stu-id="ff394-120">srv_paramlen</span></span>](srv-sendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-121">srv_parammaxlen</span><span class="sxs-lookup"><span data-stu-id="ff394-121">srv_parammaxlen</span></span>](srv-sendrow-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-122">srv_paramname</span><span class="sxs-lookup"><span data-stu-id="ff394-122">srv_paramname</span></span>](srv-setcoldata-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-123">srv_paramnumber</span><span class="sxs-lookup"><span data-stu-id="ff394-123">srv_paramnumber</span></span>](srv-setcollen-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-124">srv_paramset</span><span class="sxs-lookup"><span data-stu-id="ff394-124">srv_paramset</span></span>](srv-setutype-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-125">srv_paramsetoutput</span><span class="sxs-lookup"><span data-stu-id="ff394-125">srv_paramsetoutput</span></span>](srv-willconvert-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-126">srv_paramstatus</span><span class="sxs-lookup"><span data-stu-id="ff394-126">srv_paramstatus</span></span>](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="ff394-127">srv_paramtype</span><span class="sxs-lookup"><span data-stu-id="ff394-127">srv_paramtype</span></span>](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
