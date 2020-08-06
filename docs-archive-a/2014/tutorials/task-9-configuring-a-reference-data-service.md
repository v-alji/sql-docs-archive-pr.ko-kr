---
title: '작업 9: 참조 데이터 서비스 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742644"
---
# <a name="task-9-configuring-a-reference-data-service"></a><span data-ttu-id="b7a08-102">태스크 9: 참조 데이터 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="b7a08-102">Task 9: Configuring a Reference Data Service</span></span>
  <span data-ttu-id="b7a08-103">이 태스크에서는 Azure Marketplace에서 참조 데이터 서비스를 사용 하도록 DQS를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-103">In this task, you configure DQS to use a Reference Data Service on Azure Marketplace.</span></span> <span data-ttu-id="b7a08-104">다음 태스크에서는이 서비스를 사용 하도록 **주소 유효성 검사** 도메인을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-104">In the next task, you will configure the **Address Validation** domain to use this service.</span></span> <span data-ttu-id="b7a08-105">런타임에 정리 작업을 수행 하는 동안 DQS는 **주소 유효성 검사** 도메인의 도메인 값을 정리를 위해 서비스에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-105">At runtime, during cleansing activity, DQS passes the values of domains in the **Address Validation** domain to the service for cleansing.</span></span> <span data-ttu-id="b7a08-106">자세한 내용은 [참조 데이터를 사용 하도록 DQS 구성을](https://msdn.microsoft.com/library/hh213070.aspx) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7a08-106">See [Configure DQS to Use Reference Data](https://msdn.microsoft.com/library/hh213070.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="b7a08-107">**DQS 클라이언트**의 기본 페이지에 있는 **관리** 창에서 **구성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-107">In the main page of **DQS Client**, in the **Administration** pane, click **Configuration**.</span></span>  
  
2.  <span data-ttu-id="b7a08-108">**참조 데이터** 탭이 활성 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-108">Ensure that **Reference Data** tab is active.</span></span>  
  
3.  <span data-ttu-id="b7a08-109">프록시 서버를 사용 하 여 인터넷에 연결 해야 하는 경우 **네트워크 설정** 영역에서 **프록시 서버** 및 **포트** 필드에 적절 한 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-109">In the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** fields if you need to use a proxy server to connect to Internet.</span></span>  
  
4.  <span data-ttu-id="b7a08-110">**DataMarket 계정 ID** 필드에 대 한 **Azure Marketplace 계정 키** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-110">Type your **Azure Marketplace Account Key** for the **DataMarket Account ID** field.</span></span>  
  
     <span data-ttu-id="b7a08-111">![Azure 데이터 마켓 참조 데이터 서비스 계정](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure 데이터 마켓 참조 데이터 서비스 계정")</span><span class="sxs-lookup"><span data-stu-id="b7a08-111">![Azure Data Market Reference Data Service Account](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market Reference Data Service Account")</span></span>  
  
5.  <span data-ttu-id="b7a08-112">텍스트 상자 옆 **의 유효성 검사** 단추를 클릭 하 여 계정 ID의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-112">Click **Validate** button next to the text box to validate the account ID.</span></span>  
  
6.  <span data-ttu-id="b7a08-113">메시지 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-113">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="b7a08-114">페이지 맨 아래에 있는 **닫기** 를 클릭 하 여 DQS 클라이언트의 기본 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7a08-114">Click **Close** at the bottom of the page to switch to the main page of DQS Client.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="b7a08-115">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="b7a08-115">Next Task</span></span>  
 [<span data-ttu-id="b7a08-116">태스크 10: 참조 데이터 서비스를 사용하도록 복합 도메인 구성</span><span class="sxs-lookup"><span data-stu-id="b7a08-116">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
