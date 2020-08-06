---
title: 로그인 감사 구성(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7e05f6c254e098a67a5ce00435c009cd450af44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660816"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a><span data-ttu-id="00303-102">로그인 감사 구성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="00303-102">Configure Login Auditing (SQL Server Management Studio)</span></span>
  <span data-ttu-id="00303-103">이 항목에서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 로그인 작업을 모니터링하도록 로그인 감사를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-103">This topic describes how to configure login auditing in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] to monitor [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] login activity.</span></span> <span data-ttu-id="00303-104">로그인 감사를 구성하여 다음 이벤트의 오류 로그에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00303-104">Login auditing can be configured to write to the error log on the following events.</span></span>  
  
-   <span data-ttu-id="00303-105">실패한 로그인</span><span class="sxs-lookup"><span data-stu-id="00303-105">Failed logins</span></span>  
  
-   <span data-ttu-id="00303-106">성공한 로그인</span><span class="sxs-lookup"><span data-stu-id="00303-106">Successful logins</span></span>  
  
-   <span data-ttu-id="00303-107">실패한 로그인과 성공한 로그인 모두</span><span class="sxs-lookup"><span data-stu-id="00303-107">Both failed and successful logins</span></span>  
  
 <span data-ttu-id="00303-108">이 옵션을 적용하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-108">You must restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before this option will take effect.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="00303-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="00303-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-login-auditing"></a><span data-ttu-id="00303-110">로그인 감사를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="00303-110">To configure login auditing</span></span>  
  
1.  <span data-ttu-id="00303-111">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 사용하여 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-111">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="00303-112">개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-112">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="00303-113">**보안** 페이지의 **로그인 감사** 에서 원하는 옵션을 클릭하고 **서버 속성** 페이지를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="00303-113">On the **Security** page, under **Login** auditing, click the desired option and close the **Server Properties** page.</span></span>  
  
4.  <span data-ttu-id="00303-114">개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-114">In Object Explorer, right-click the server name, and then click **Restart**.</span></span>  
  
  
