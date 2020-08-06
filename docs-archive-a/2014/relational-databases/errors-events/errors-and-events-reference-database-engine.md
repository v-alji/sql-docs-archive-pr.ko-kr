---
title: 오류 및 이벤트 참조(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server Database Engine]
- Database Engine [SQL Server], errors
- events [SQL Server Database Engine]
ms.assetid: ea928535-6fd1-4738-a8ed-ffb602f3825e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e991accfd0e6fdd4fa25746499308455eff85ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735292"
---
# <a name="errors-and-events-reference-database-engine"></a><span data-ttu-id="9df6d-102">오류 및 이벤트 참조(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="9df6d-102">Errors and Events Reference (Database Engine)</span></span>

<span data-ttu-id="9df6d-103">이 섹션에는 추가 설명이 필요한 데이터베이스 엔진 오류 메시지가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-103">This section contains selected Database Engine error messages that need further explanation.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="9df6d-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9df6d-104">In This Section</span></span>  
 <span data-ttu-id="9df6d-105">[이벤트 및 오류 데이터베이스 엔진](database-engine-events-and-errors.md) 오류 메시지의 형식을 설명 하 고 오류 메시지를 보고 오류 메시지를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 응용 프로그램에 반환 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-105">[Database Engine Events and Errors](database-engine-events-and-errors.md) Describes the format of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages and explains how to view error messages and return error messages to applications.</span></span>  
  
 <span data-ttu-id="9df6d-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 오류 메시지, 가능한 원인, 문제 해결을 위해 수행할 수 있는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-106">Provides an explanation of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9df6d-107">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="9df6d-107">External Resources</span></span>  
 <span data-ttu-id="9df6d-108">제품 설명서나 웹에서 필요한 정보를 찾지 못한 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커뮤니티에 질문을 올리거나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 지원 서비스에 도움을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-108">If you have not found the information you are looking for in the product documentation or on the Web, you can either ask a question in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community or request help from [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="9df6d-109">다음 표에서는 링크와 해당 리소스에 대한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-109">The following table links to and describes these resources.</span></span>  
  
|<span data-ttu-id="9df6d-110">리소스</span><span class="sxs-lookup"><span data-stu-id="9df6d-110">Resource</span></span>|<span data-ttu-id="9df6d-111">Description</span><span class="sxs-lookup"><span data-stu-id="9df6d-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="9df6d-112">SQL Server 커뮤니티</span><span class="sxs-lookup"><span data-stu-id="9df6d-112">SQL Server Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42455)|<span data-ttu-id="9df6d-113">이 사이트에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커뮤니티에서 모니터링하는 뉴스 그룹과 포럼에 대한 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-113">This site has links to newsgroups and forums monitored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community.</span></span> <span data-ttu-id="9df6d-114">또한 블로그와 웹 사이트와 같은 커뮤니티 정보 출처가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-114">It also lists community information sources, such as blogs and Web sites.</span></span> <span data-ttu-id="9df6d-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커뮤니티를 통해 답변을 받지 못하는 경우도 있지만 이 커뮤니티는 질문에 대한 답변을 얻는 데 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community is very helpful in answering questions, although an answer cannot be guaranteed.</span></span>|  
|[<span data-ttu-id="9df6d-116">SQL Server Developer Center 커뮤니티</span><span class="sxs-lookup"><span data-stu-id="9df6d-116">SQL Server Developer Center Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42456)|<span data-ttu-id="9df6d-117">이 사이트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개발자에게 유용한 뉴스 그룹, 포럼 및 기타 커뮤니티 리소스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-117">This site focuses on the newsgroups, forums, and other community resources that are useful to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] developers.</span></span>|  
|[<span data-ttu-id="9df6d-118">Microsoft 도움말 및 지원</span><span class="sxs-lookup"><span data-stu-id="9df6d-118">Microsoft Help and Support</span></span>](https://go.microsoft.com/fwlink/?linkid=16419)|<span data-ttu-id="9df6d-119">이 웹 사이트에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 전문가의 상담을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-119">You can use this Web site to open a case with a [!INCLUDE[msCoName](../../includes/msconame-md.md)] support professional.</span></span>|  
  
  
