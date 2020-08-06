---
title: 경고에 대한 호출기 주소 형식 지정 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471f9a4958f51491b312d89239a2204c907e25e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639222"
---
# <a name="format-pager-addresses-for-alerts"></a><span data-ttu-id="515f0-102">Format Pager Addresses for Alerts</span><span class="sxs-lookup"><span data-stu-id="515f0-102">Format Pager Addresses for Alerts</span></span>
  <span data-ttu-id="515f0-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 경고의 호출기 주소 형식을 지정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="515f0-103">This topic describes how to format pager addresses for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="515f0-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="515f0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="515f0-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="515f0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="515f0-106">보안</span><span class="sxs-lookup"><span data-stu-id="515f0-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="515f0-107">**다음을 사용하여 호출기 주소의 형식을 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="515f0-107">**To format pager addresses, using:**</span></span>  
  
     [<span data-ttu-id="515f0-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="515f0-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="515f0-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="515f0-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="515f0-110">보안</span><span class="sxs-lookup"><span data-stu-id="515f0-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="515f0-111">권한</span><span class="sxs-lookup"><span data-stu-id="515f0-111">Permissions</span></span>  
 <span data-ttu-id="515f0-112">기본적으로 **sysadmin** 고정 서버 역할의 멤버가 경고의 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-112">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="515f0-113">다른 사용자는 **msdb** 데이터베이스의 **SQLAgentOperatorRole** 고정 데이터베이스 역할을 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-113">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="515f0-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="515f0-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-format-pager-addresses"></a><span data-ttu-id="515f0-115">호출기 주소의 형식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="515f0-115">To format pager addresses</span></span>  
  
1.  <span data-ttu-id="515f0-116">**개체 탐색기**에서 더하기 기호를 클릭하여 호출기에 전송하려는 경고가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-116">In **Object Explorer**, click the plus sign to expand the server that contains the alert that you want to send to a pager.</span></span>  
  
2.  <span data-ttu-id="515f0-117">**SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-117">Right-click **SQL Server Agent** and select **Properties**</span></span>  
  
3.  <span data-ttu-id="515f0-118">**페이지 선택**아래에서 **경고 시스템**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-118">Under **Select a page**, select **Alert System**.</span></span>  
  
4.  <span data-ttu-id="515f0-119">**호출기 전자 메일 주소 형식** 필드의 **받는 사람 줄** 및 **참조 줄** 상자에 호출기 주소 접두사나 접미사를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-119">In the **To line** and **CC line** boxes of the **Address formatting for pager e-mails** field, enter the pager address prefix or suffix.</span></span> <span data-ttu-id="515f0-120">알림이 보내질 때 운영자의 실제 호출기 주소가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-120">The operator's actual pager address is inserted when a notification is sent.</span></span>  
  
5.  <span data-ttu-id="515f0-121">**제목** 상자에 제목 줄 접두사나 접미사를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-121">In the **Subject** box, enter the subject line prefix or suffix.</span></span>  
  
6.  <span data-ttu-id="515f0-122">**알림 페이지에 전자 메일 본문 포함** 확인란을 선택하여 호출기 메시지와 함께 제목 줄만이 아닌 전체 전자 메일 메시지를 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-122">Select the **Include body of e-mail in notification page** check box to include the full e-mail message with the pager message (as opposed to the subject line only).</span></span>  
  
7.  <span data-ttu-id="515f0-123">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="515f0-123">When finished, click **OK**.</span></span>  
  
  
