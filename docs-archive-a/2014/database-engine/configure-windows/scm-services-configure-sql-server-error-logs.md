---
title: SQL Server 오류 로그 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661357"
---
# <a name="configure-sql-server-error-logs"></a><span data-ttu-id="8789d-102">SQL Server 오류 로그 구성</span><span class="sxs-lookup"><span data-stu-id="8789d-102">Configure SQL Server Error Logs</span></span>
  <span data-ttu-id="8789d-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그의 재활용 방법을 확인하거나 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-103">This topic describes how to view or modify the way [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs are recycled.</span></span>  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a><span data-ttu-id="8789d-104">SQL Server 오류 로그 구성 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="8789d-104">To open the Configure SQL Server Error Logs dialog box</span></span>  
  
1.  <span data-ttu-id="8789d-105">개체 탐색기에서 SQL Server 인스턴스를 확장하고 **관리**를 확장한 다음 **SQL Server 로그**를 마우스 오른쪽 단추로 클릭하고 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-105">In Object Explorer, expand the instance of SQL Server, expand **Management**, right-click **SQL Server Logs**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="8789d-106">**SQL Server 오류 로그 구성** 대화 상자의 다음 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-106">In the **Configure SQL Server Error Logs** dialog box, choose from the following options.</span></span>  
  
     <span data-ttu-id="8789d-107">**재활용 이전의 오류 로그 파일 수 제한**</span><span class="sxs-lookup"><span data-stu-id="8789d-107">**Limit the number of the error log files before they are recycled**</span></span>  
     <span data-ttu-id="8789d-108">재활용하기 전의 오류 로그 수 제한을 두려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-108">Check to limit the number of error logs created before they are recycled.</span></span> <span data-ttu-id="8789d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작할 때마다 오류 로그가 새로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-109">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8789d-110">는 최근 6개 로그의 백업을 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-110">retains backups of the previous six logs, unless you check this option, and specify a different maximum number of error log files below.</span></span>  
  
     <span data-ttu-id="8789d-111">**최대 오류 로그 파일 수**</span><span class="sxs-lookup"><span data-stu-id="8789d-111">**Maximum number of error log files**</span></span>  
     <span data-ttu-id="8789d-112">재활용하기 전의 오류 로그 파일 최대 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-112">Specify the maximum number of error log files created before they are recycled.</span></span> <span data-ttu-id="8789d-113">기본값은 6이며 이 값은 백업 로그를 재활용하기까지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 보유하는 이전 백업 로그의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8789d-113">The default is 6, which is the number of previous backup logs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains before recycling them.</span></span>  
  
  
