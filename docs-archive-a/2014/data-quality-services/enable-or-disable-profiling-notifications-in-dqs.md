---
title: DQS에서 프로파일링 알림 설정 또는 해제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b3b5e8cec1cac3eb1ce4357480c0f994a33d4c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732051"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a><span data-ttu-id="24bf9-102">DQS에서 프로파일링 알림 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="24bf9-102">Enable or Disable Profiling Notifications in DQS</span></span>
  <span data-ttu-id="24bf9-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 프로파일링 알림을 설정하거나 해제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-103">This topic describes how to enable or disable profiling notifications in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="24bf9-104">기본적으로 프로파일링 알림은 DQS에서 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-104">By default, profiling notifications are enabled in DQS.</span></span> <span data-ttu-id="24bf9-105">프로파일링 알림은 데이터 원본에 대한 중요한 사실과 데이터에 대해 수행된 현재 작업의 효과를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-105">Profiling notifications tell you important facts about the data source and the effectiveness of the current activity performed on the data.</span></span> <span data-ttu-id="24bf9-106">자세한 내용은 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24bf9-106">For more information, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24bf9-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="24bf9-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="24bf9-108">보안</span><span class="sxs-lookup"><span data-stu-id="24bf9-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="24bf9-109">권한</span><span class="sxs-lookup"><span data-stu-id="24bf9-109">Permissions</span></span>  
 <span data-ttu-id="24bf9-110">알림을 설정하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-110">You must have the dqs_administrator role on the DQS_MAIN database to enable notifications.</span></span>  
  
##  <a name="enable-or-disable-profiling-notifications"></a><a name="Enable"></a><span data-ttu-id="24bf9-111">프로 파일링 알림 사용 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="24bf9-111">Enable or Disable Profiling Notifications</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="24bf9-112">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="24bf9-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="24bf9-114">그런 다음 **일반 설정** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-114">Next, click the **General Settings** tab.</span></span>  
  
4.  <span data-ttu-id="24bf9-115">**알림 사용** 확인란을 선택하거나 선택 취소하여 DQS에서의 여러 작업에 대해 프로파일링 알림을 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-115">Clear or select the **Enable Notifications** check box to disable or enable profiling notifications for various activities in DQS.</span></span>  
  
5.  <span data-ttu-id="24bf9-116">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24bf9-116">Click **Close**.</span></span>  
  
  
