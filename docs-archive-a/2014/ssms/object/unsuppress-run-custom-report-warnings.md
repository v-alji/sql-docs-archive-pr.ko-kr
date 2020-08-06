---
title: 사용자 지정 보고서 실행 경고 표시 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
ms.openlocfilehash: 725362ff7f8a6c282529f652e8813a8083257eb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727856"
---
# <a name="unsuppress-run-custom-report-warnings"></a><span data-ttu-id="b25f2-102">사용자 지정 보고서 실행 경고 표시</span><span class="sxs-lookup"><span data-stu-id="b25f2-102">Unsuppress Run Custom Report Warnings</span></span>
  <span data-ttu-id="b25f2-103">사용자 지정 보고서에 대한 경고 대화 상자에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-103">There are two warning dialog boxes for custom reports.</span></span> <span data-ttu-id="b25f2-104">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이러한 상자를 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-104">This topic describes how to unsuppress the display of these boxes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b25f2-105">기본적으로 사용자 지정 보고서가 실행되기 전에 **사용자 지정 보고서 실행** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-105">By default, the **Run Custom Reports** dialog box appears before a custom report runs.</span></span> <span data-ttu-id="b25f2-106">**이 경고 메시지를 다시 표시 안 함** 확인란을 선택하면 이 대화 상자가 더 이상 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-106">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span> <span data-ttu-id="b25f2-107">또한 사용자 지정 보고서를 연 다음 링크를 클릭하여 다른 사용자 지정 보고서를 열면 기본적으로 **사용자 지정 보고서 실행** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-107">Also by default, the **Run Custom Reports** dialog box appears when you open a custom report and then click a link to open another custom report.</span></span> <span data-ttu-id="b25f2-108">이 대화 상자는 드릴스루 사용자 지정 보고서 파일에 대한 채우기 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-108">This dialog box displays the fill path to the drill-through custom report file.</span></span> <span data-ttu-id="b25f2-109">**이 경고 메시지를 다시 표시 안 함** 확인란을 선택하면 이 대화 상자가 더 이상 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-109">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b25f2-110">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b25f2-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a><span data-ttu-id="b25f2-111">주 사용자 지정 보고서 경고 대화 상자를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="b25f2-111">To unsuppress the main custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="b25f2-112">\<*Server*> \\ < *Share* >| \<*Drive*> \Documents 및 설정 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-112">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="b25f2-113">를 마우스 오른쪽 단추로 클릭 한 `reports.xml` 다음 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-113">Right-click `reports.xml`, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="b25f2-114">\*\* \<SuppressWarning> True \</SuppressWarning> 를 \<SuppressWarning> false \</SuppressWarning> 로\*\*변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-114">Change**\<SuppressWarning>true\</SuppressWarning> to \<SuppressWarning>false\</SuppressWarning>**.</span></span>  
  
4.  <span data-ttu-id="b25f2-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-115">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a><span data-ttu-id="b25f2-116">드릴스루 사용자 지정 보고서 경고 대화 상자를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="b25f2-116">To unsuppress the drill-through custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="b25f2-117">\<*Server*> \\ < *Share* >| \<*Drive*> \Documents 및 설정 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-117">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="b25f2-118">를 마우스 오른쪽 단추로 클릭 `reports.xml` 하 고 **편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-118">Right-click `reports.xml`, and click **Edit**.</span></span>  
  
3.  <span data-ttu-id="b25f2-119">\*\* \<SuppressDrillthroughWarning> True \</SuppressDrillthroughWarning> 를 \<SuppressDrillthroughWarning> false \</SuppressDrillthroughWarning> 로\*\*변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-119">Change **\<SuppressDrillthroughWarning>true\</SuppressDrillthroughWarning>to \<SuppressDrillthroughWarning>false\</SuppressDrillthroughWarning>**.</span></span>  
  
4.  <span data-ttu-id="b25f2-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b25f2-120">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25f2-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b25f2-121">See Also</span></span>  
 <span data-ttu-id="b25f2-122">[Management Studio의 사용자 지정 보고서](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b25f2-122">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="b25f2-123">[Management Studio에 사용자 지정 보고서 추가](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b25f2-123">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 [<span data-ttu-id="b25f2-124">개체 탐색기 노드 속성과 함께 사용자 지정 보고서 사용</span><span class="sxs-lookup"><span data-stu-id="b25f2-124">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
