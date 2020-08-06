---
title: '1단원: 샘플 구독자 데이터베이스 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742911"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a><span data-ttu-id="4c7e9-102">1단원: 샘플 구독자 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="4c7e9-102">Lesson 1: Creating a Sample Subscriber Database</span></span>
  <span data-ttu-id="4c7e9-103">데이터 기반 구독을 정의하려면 먼저 구독 데이터를 제공하는 데이터 원본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-103">Before you can define a data-driven subscription, you must have a data source that provides subscription data.</span></span> <span data-ttu-id="4c7e9-104">이 단계에서는 이 자습서에 사용되는 구독 데이터를 저장할 소규모 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-104">In this step, you will create a small database to store the subscription data used in this tutorial.</span></span> <span data-ttu-id="4c7e9-105">나중에 구독을 처리할 때 보고서 서버에서는 이 데이터를 검색하여 보고서 출력, 배달 옵션 및 보고서 표시 형식을 사용자 지정하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-105">Later, when the subscription is processed, the report server retrieves this data and uses it to customize report output, delivery options, and report presentation format.</span></span>  
  
 <span data-ttu-id="4c7e9-106">이 단원에서는를 사용 하 여 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 데이터베이스를 만드는 것으로 가정 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-106">This lesson assumes you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to create a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span>  
  
### <a name="to-create-a-sample-subscriber-database"></a><span data-ttu-id="4c7e9-107">예제 구독자 데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4c7e9-107">To create a sample Subscriber database</span></span>  
  
1.  <span data-ttu-id="4c7e9-108">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]를 시작한 다음 [!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-108">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and open a connection to a [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4c7e9-109">데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-109">Right-click on Databases, select **New Database...**.</span></span>  
  
3.  <span data-ttu-id="4c7e9-110">새 데이터베이스 대화 상자의 데이터베이스 이름에 *구독자*를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-110">In the New Database dialog box, in Database Name, type *Subscribers*.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="4c7e9-111">도구 모음에서 **새 쿼리** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-111">Click the **New Query** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="4c7e9-112">다음 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-112">Copy the following [!INCLUDE[tsql](../includes/tsql-md.md)] statements into the empty query:</span></span>  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  <span data-ttu-id="4c7e9-113">**! 실행** 을 도구 모음에서 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-113">Click **! Execute** on the toolbar.</span></span>  
  
7.  <span data-ttu-id="4c7e9-114">SELECT 문을 사용하여 세 개의 데이터 행이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-114">Use a SELECT statement to verify that you have three rows of data.</span></span> <span data-ttu-id="4c7e9-115">예: `select * from OrderInfo`</span><span class="sxs-lookup"><span data-stu-id="4c7e9-115">For example: `select * from OrderInfo`</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4c7e9-116">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4c7e9-116">Next Steps</span></span>  
 <span data-ttu-id="4c7e9-117">보고서 배포를 추진하고 구독자마다 보고서 출력을 다르게 할 구독 데이터를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-117">You have successfully created the subscription data that will drive report distribution and vary the report output for each subscriber.</span></span> <span data-ttu-id="4c7e9-118">다음 단원에서는 구독자에게 배포할 보고서의 데이터 원본 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-118">Next, you will modify the data source properties of the report you will distribute to subscribers.</span></span> <span data-ttu-id="4c7e9-119">데이터 원본 속성 수정은 데이터 기반 구독 배달에 사용할 보고서를 준비하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-119">Modifying the data source properties is done to prepare the report for data-driven subscription delivery.</span></span> <span data-ttu-id="4c7e9-120">또한 구독에서 구독자 데이터와 함께 사용할 매개 변수를 포함하도록 보고서 디자인을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7e9-120">You will also modify the report design to include a parameter that the subscription will use with the subscriber data.</span></span> <span data-ttu-id="4c7e9-121">[2 단원: 보고서 데이터 원본 속성 수정](lesson-2-modifying-the-report-data-source-properties.md)</span><span class="sxs-lookup"><span data-stu-id="4c7e9-121">[Lesson 2: Modifying the Report Data Source Properties](lesson-2-modifying-the-report-data-source-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7e9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c7e9-122">See Also</span></span>  
 <span data-ttu-id="4c7e9-123">[데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="4c7e9-123">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="4c7e9-124">[데이터베이스 만들기](../relational-databases/databases/create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="4c7e9-124">[Create a Database](../relational-databases/databases/create-a-database.md) </span></span>  
 [<span data-ttu-id="4c7e9-125">기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="4c7e9-125">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
