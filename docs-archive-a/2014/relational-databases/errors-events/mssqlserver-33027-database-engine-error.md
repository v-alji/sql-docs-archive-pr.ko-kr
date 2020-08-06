---
title: MSSQLSERVER_33027 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f6bb461b42b66368224fffd2c14f9b4da61abf5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650058"
---
# <a name="mssqlserver_33027"></a><span data-ttu-id="09b18-102">MSSQLSERVER_33027</span><span class="sxs-lookup"><span data-stu-id="09b18-102">MSSQLSERVER_33027</span></span>
    
## <a name="details"></a><span data-ttu-id="09b18-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="09b18-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09b18-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="09b18-104">Product Name</span></span>|<span data-ttu-id="09b18-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="09b18-105">SQL Server</span></span>|  
|<span data-ttu-id="09b18-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="09b18-106">Event ID</span></span>|<span data-ttu-id="09b18-107">33027</span><span class="sxs-lookup"><span data-stu-id="09b18-107">33027</span></span>|  
|<span data-ttu-id="09b18-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="09b18-108">Event Source</span></span>|<span data-ttu-id="09b18-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="09b18-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="09b18-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="09b18-110">Component</span></span>|<span data-ttu-id="09b18-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="09b18-111">SQLEngine</span></span>|  
|<span data-ttu-id="09b18-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="09b18-112">Symbolic Name</span></span>|<span data-ttu-id="09b18-113">SEC_CRYPTOPROV_CANTLOADDLL</span><span class="sxs-lookup"><span data-stu-id="09b18-113">SEC_CRYPTOPROV_CANTLOADDLL</span></span>|  
|<span data-ttu-id="09b18-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="09b18-114">Message Text</span></span>|<span data-ttu-id="09b18-115">잘못된 Authenticode 서명 또는 잘못된 파일 경로로 인해 암호화 공급자 '%.\*ls'을(를) 로드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="09b18-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span> <span data-ttu-id="09b18-116">다른 오류가 있는지 이전 메시지를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="09b18-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="09b18-117">설명</span><span class="sxs-lookup"><span data-stu-id="09b18-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="09b18-118">에서 DLL을 로드할 수 없어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 위의 오류 메시지에 나열된 암호화 공급자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09b18-118">was unable to use the cryptographic provider listed in the error message, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not load the DLL.</span></span> <span data-ttu-id="09b18-119">이름이 잘못되었거나 Authenticode 서명이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="09b18-119">Either the name is invalid or the Authenticode signature is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="09b18-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="09b18-120">User Action</span></span>  
 <span data-ttu-id="09b18-121">파일이 있고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 해당 위치에 액세스할 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="09b18-121">Check that the file is present and that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has permission to access that location.</span></span> <span data-ttu-id="09b18-122">오류 로그에서 관련된 다른 메시지를 확인하거나</span><span class="sxs-lookup"><span data-stu-id="09b18-122">Check the error log for additional related messages.</span></span> <span data-ttu-id="09b18-123">암호화 공급자에게 자세한 정보를 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="09b18-123">Otherwise, contact the cryptographic provider for more information.</span></span>  
  
  
