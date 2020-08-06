---
title: SQL Server 에이전트 속성(작업 시스템 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 743a8d558e97e9ad83cfc66e9ef1adf2e1bc0c2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659771"
---
# <a name="sql-server-agent-properties-job-system-page"></a><span data-ttu-id="ceb90-102">SQL Server 에이전트 속성(작업 시스템 페이지)</span><span class="sxs-lookup"><span data-stu-id="ceb90-102">SQL Server Agent Properties (Job System Page)</span></span>
  <span data-ttu-id="ceb90-103">이 페이지를 사용 하 여 에이전트 서비스에서 작업을 관리 하는 방법을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-103">Use this page to view and modify how the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service manages jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ceb90-104">옵션</span><span class="sxs-lookup"><span data-stu-id="ceb90-104">Options</span></span>  
 <span data-ttu-id="ceb90-105">**시스템 종료 제한 시간 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="ceb90-105">**Shutdown time-out interval (in seconds)**</span></span>  
 <span data-ttu-id="ceb90-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 종료 전 작업 완료 대기 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-106">Specifies the number of seconds that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for jobs to complete before shutting down.</span></span> <span data-ttu-id="ceb90-107">지정한 간격을 초과하여 작업이 실행되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 강제로 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-107">If the job is still running after the interval specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent forcefully stops the job.</span></span>  
  
 <span data-ttu-id="ceb90-108">**비관리자 프록시 계정 사용**</span><span class="sxs-lookup"><span data-stu-id="ceb90-108">**Use a non-administrator proxy account**</span></span>  
 <span data-ttu-id="ceb90-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 대한 비관리자 프록시 계정을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-109">Sets a non-administrator proxy account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ceb90-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]이상 버전에서는 여러 프록시를 지원 하므로이 옵션은 관리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하는 경우에만 적용 됩니다. 이전 버전의 에이전트 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb90-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="ceb90-111">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="ceb90-111">**User name**</span></span>  
 <span data-ttu-id="ceb90-112">비관리자 프록시 계정에 대한 사용자의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-112">Type the name of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ceb90-113">에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-113">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="ceb90-114">**암호**</span><span class="sxs-lookup"><span data-stu-id="ceb90-114">**Password**</span></span>  
 <span data-ttu-id="ceb90-115">비관리자 프록시 계정에 대한 사용자의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-115">Type the password of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="ceb90-116">이상 버전에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-116">and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="ceb90-117">**도메인**</span><span class="sxs-lookup"><span data-stu-id="ceb90-117">**Domain**</span></span>  
 <span data-ttu-id="ceb90-118">비관리자 프록시 계정에 대한 사용자의 도메인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-118">Type the domain of the user for the non-administrative proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ceb90-119">에서는 여러 프록시를 지원하므로 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에이전트를 관리할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb90-119">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb90-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ceb90-120">See Also</span></span>  
 [<span data-ttu-id="ceb90-121">작업 구현</span><span class="sxs-lookup"><span data-stu-id="ceb90-121">Implement Jobs</span></span>](implement-jobs.md)  
  
  
