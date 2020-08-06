---
title: MSSQLSERVER_26014 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8114183b212767d01013eee9387d8b2efa2e0d7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651034"
---
# <a name="mssqlserver_26014"></a><span data-ttu-id="7f19f-102">MSSQLSERVER_26014</span><span class="sxs-lookup"><span data-stu-id="7f19f-102">MSSQLSERVER_26014</span></span>
    
## <a name="details"></a><span data-ttu-id="7f19f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7f19f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f19f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7f19f-104">Product Name</span></span>|<span data-ttu-id="7f19f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f19f-105">SQL Server</span></span>|  
|<span data-ttu-id="7f19f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7f19f-106">Event ID</span></span>|<span data-ttu-id="7f19f-107">26014</span><span class="sxs-lookup"><span data-stu-id="7f19f-107">26014</span></span>|  
|<span data-ttu-id="7f19f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7f19f-108">Event Source</span></span>|<span data-ttu-id="7f19f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7f19f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7f19f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7f19f-110">Component</span></span>|<span data-ttu-id="7f19f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7f19f-111">SQLEngine</span></span>|  
|<span data-ttu-id="7f19f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7f19f-112">Symbolic Name</span></span>|<span data-ttu-id="7f19f-113">SNI_SSL_USER_CERT_FAILURE</span><span class="sxs-lookup"><span data-stu-id="7f19f-113">SNI_SSL_USER_CERT_FAILURE</span></span>|  
|<span data-ttu-id="7f19f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7f19f-114">Message Text</span></span>|<span data-ttu-id="7f19f-115">사용자 지정 인증서 [인증서 해시(sha1) "%hs"]을(를) 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-115">Unable to load user-specified certificate [Cert Hash(sha1) "%hs"].</span></span> <span data-ttu-id="7f19f-116">서버가 연결을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-116">The server will not accept a connection.</span></span> <span data-ttu-id="7f19f-117">인증서가 제대로 설치되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-117">You should verify that the certificate is correctly installed.</span></span> <span data-ttu-id="7f19f-118">온라인 설명서에서 "SSL에 사용되는 인증서 구성"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7f19f-118">See "Configuring Certificate for Use by SSL" in Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7f19f-119">설명</span><span class="sxs-lookup"><span data-stu-id="7f19f-119">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="7f19f-120">에서 메시지에 명명된 인증서를 로드하려고 시도했지만 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-120">attempted to load the certificate named in the message but the operation failed.</span></span> <span data-ttu-id="7f19f-121">이 문제를 해결해야 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 이 인증서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-121">This problem must be resolved before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use this certificate.</span></span>  
  
 <span data-ttu-id="7f19f-122">가능한 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-122">Possible causes of the error include:</span></span>  
  
-   <span data-ttu-id="7f19f-123">인증서가 이동되었거나 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-123">The certificate could have been moved or deleted.</span></span>  
  
-   <span data-ttu-id="7f19f-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용하는 로그인이 변경된 경우 인증서에 액세스하는 데 필요한 사용 권한이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-124">If the login used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has changed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not have permission to access the certificate.</span></span>  
  
-   <span data-ttu-id="7f19f-125">인증서가 만료되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f19f-125">The certificate may have expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f19f-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7f19f-126">User Action</span></span>  
 <span data-ttu-id="7f19f-127">메시지에 명명된 인증서가 시스템에 있는지, 액세스 가능한지, 사용할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="7f19f-127">Make sure the certificate named in the message exists on the system, is accessible, and it is valid for use.</span></span>  
  
  
