---
title: 대상 서버를 강제 실행하여 마스터 서버 폴링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
ms.openlocfilehash: b37bf19bfe8e8fb55c29c8d94c28a341d06df5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639226"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a><span data-ttu-id="f46ed-102">Force a Target Server to Poll the Master Server</span><span class="sxs-lookup"><span data-stu-id="f46ed-102">Force a Target Server to Poll the Master Server</span></span>
  <span data-ttu-id="f46ed-103">이 항목에서는 강제로 대상 서버가 마스터 서버를 폴링하도록 하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-103">This topic describes how to force a target server to poll the master server.</span></span> <span data-ttu-id="f46ed-104">대상 서버는 마스터 서버에 등록된 서버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-104">The target server must be a registered server on the master server.</span></span>  
  
 <span data-ttu-id="f46ed-105">작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 수행하도록 지정된 일련의 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-105">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="f46ed-106">다중 서버 작업은 마스터 서버가 하나 이상의 대상 서버에서 실행하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-106">A multiserver job is a job that a master server runs on one or more target servers.</span></span> <span data-ttu-id="f46ed-107">각 대상 서버는 같은 작업의 한 인스턴스를 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-107">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="f46ed-108">각 대상 서버는 주기적으로 마스터 서버를 폴링하여 해당 대상 서버에 새로 할당된 작업의 복사본을 다운로드한 다음 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-108">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="f46ed-109">대상 서버는 로컬에서 작업을 실행한 다음 마스터 서버에 다시 연결하여 작업 결과 상태를 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-109">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f46ed-110">대상 서버에서 작업 상태 업로드를 시도할 때 마스터 서버가 액세스 가능하지 않은 경우 작업 상태는 마스터 서버가 액세스 가능해질 때까지 스풀링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-110">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
-   <span data-ttu-id="f46ed-111">**시작하기 전 주의 사항:**  [제한 사항](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="f46ed-111">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="f46ed-112">**대상 서버가 마스터 서버를 폴링하도록 설정하려면**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="f46ed-112">**To force a target server to poll the master server, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f46ed-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f46ed-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f46ed-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f46ed-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f46ed-115">대상 서버는 마스터 서버에 등록된 서버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-115">The target server must be a registered server on the master server.</span></span> <span data-ttu-id="f46ed-116">마스터 서버에서 이 항목에 제공된 지침을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-116">You must run the instructions given in this topic from the master server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f46ed-117">보안</span><span class="sxs-lookup"><span data-stu-id="f46ed-117">Security</span></span>  
 <span data-ttu-id="f46ed-118">자세한 내용은 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 및 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f46ed-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="f46ed-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f46ed-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f46ed-120">**대상 서버가 마스터 서버를 폴링하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="f46ed-120">**To force a target server to poll the master server**</span></span>  
  
1.  <span data-ttu-id="f46ed-121">**개체 탐색기**에서 마스터 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-121">In **Object Explorer**, expand the master server.</span></span>  
  
2.  <span data-ttu-id="f46ed-122">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-122">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="f46ed-123">대상 서버를 클릭한 다음 **강제 폴링**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f46ed-123">Click a target server, and then click **Force Poll**.</span></span>  
  
  
