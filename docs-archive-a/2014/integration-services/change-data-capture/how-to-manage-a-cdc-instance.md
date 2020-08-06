---
title: CDC 인스턴스 관리 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e387b9e1a75b7279a68d1c9c9b637f5473071013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728607"
---
# <a name="how-to-manage-a-cdc-instance"></a><span data-ttu-id="220ad-102">How to Manage a CDC Instance</span><span class="sxs-lookup"><span data-stu-id="220ad-102">How to Manage a CDC Instance</span></span>
  <span data-ttu-id="220ad-103">이 절차에서는 CDC Designer 콘솔을 사용하여 런타임에 CDC 인스턴스 작업을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-103">This procedure describes how to use the CDC Designer Console to manage CDC instance operations at runtime.</span></span>  
  
### <a name="to-manage-cdc-instance-operations"></a><span data-ttu-id="220ad-104">CDC 인스턴스 작업을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="220ad-104">To manage CDC instance operations</span></span>  
  
1.  <span data-ttu-id="220ad-105">**시작** 메뉴에서 **CDC Designer 콘솔**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="220ad-106">왼쪽 창에서 **변경 데이터 캡처** 를 확장한 다음 보려는 인스턴스를 포함하는 서비스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="220ad-107">작업할 인스턴스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-107">Select the name of an instance you want to work with.</span></span>  
  
4.  <span data-ttu-id="220ad-108">CDC Designer 콘솔의 오른쪽에 있는 **동작** 창에서 수행할 작업을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-108">From the **Actions** pane on the right side of the CDC Designer Console, click on the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="220ad-109">또한 왼쪽 창에서 인스턴스의 이름을 마우스 오른쪽 단추로 클릭하고 수행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-109">You can also right-click the name of the instance in the left pane and select the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="220ad-110">다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-110">You can carry out the following tasks:</span></span>  
  
    -   <span data-ttu-id="220ad-111">**시작**: 변경 캡처를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-111">**Start**: To start capturing changes.</span></span>  
  
    -   <span data-ttu-id="220ad-112">**중지**: 변경 캡처를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-112">**Stop**: To stop capturing changes</span></span>  
  
    -   <span data-ttu-id="220ad-113">**다시 설정**: **다시 설정** 을 클릭하여 CDC 인스턴스를 초기(비어 있음) 상태로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-113">**Reset**: Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="220ad-114">이 옵션은 CDC 인스턴스가 중지된 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-114">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="220ad-115">변경 테이블의 모든 변경 사항과 CDC 인스턴스 내부 상태가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-115">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="220ad-116">CDC 인스턴스를 나중에 시작하면 변경 캡처가 해당 시점에서 시작되고 CDC 인스턴스가 시작된 후에 시작된 트랜잭션만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-116">When the CDC instance is started later on, change capture will start from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
    -   <span data-ttu-id="220ad-117">**삭제**: CDC 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-117">**Delete**: To delete the CDC instance.</span></span>  
  
    -   <span data-ttu-id="220ad-118">**Oracle 로깅 스크립트**: **Oracle 로깅 스크립트** 를 클릭하여 Oracle 로깅 스크립트 대화 상자를 Oracle 보완 로깅 스크립트와 함께 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-118">**Oracle Logging Script**: Click **Oracle Logging Script** to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="220ad-119">이 대화 상자에서 수행할 수 있는 작업에 대한 자세한 내용은 [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="220ad-119">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
         <span data-ttu-id="220ad-120">**참고**: 보완 로깅 스크립트를 실행하면 유효한 Oracle 사용자 이름과 암호를 입력할 수 있는 스크립트 실행을 위한 Oracle 자격 증명 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-120">**Note**: When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="220ad-121">적절한 Oracle 자격 증명을 제공하는 방법은 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="220ad-121">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
    -   <span data-ttu-id="220ad-122">**CDC 인스턴스 배포**: CDC 인스턴스에 대한 배포 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-122">**CDC Instance Deployment**: To generate a deployment script for the CDC Instance.</span></span> <span data-ttu-id="220ad-123">이 대화 상자에 대한 자세한 내용은 [CDC Instance Deployment Script](cdc-instance-deployment-script.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="220ad-123">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
     <span data-ttu-id="220ad-124">위의 태스크에 대한 자세한 내용은 [Manage a CDC Instance](manage-a-cdc-instance.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="220ad-124">For more information about these tasks, see [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
 <span data-ttu-id="220ad-125">또한 **속성** 을 선택하여 CDC 인스턴스 구성 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="220ad-125">You can also select **Properties** to edit the CDC instance configuration properties.</span></span> <span data-ttu-id="220ad-126">CDC 인스턴스 속성을 편집하는 방법은 [Edit Instance Properties](edit-instance-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="220ad-126">For more information about editing the CDC instance properties, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
  
