---
title: Azure HDInsight 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaf2f57fec50a58ad1b7e7578407fb6cf3fa0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728651"
---
# <a name="azure-hdinsight-connection-manager"></a><span data-ttu-id="33ee1-102">Azure HDInsight 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="33ee1-102">Azure HDInsight Connection Manager</span></span>
<span data-ttu-id="33ee1-103">**Azure HDInsight 연결 관리자**를 통해 SSIS 패키지는 Azure HDInsight 클러스터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-103">The **Azure HDInsight Connection Manager** enables an SSIS package to connect to an Azure HDInsight cluster.</span></span>

<span data-ttu-id="33ee1-104">**Azure HDInsight 연결 관리자**를 만들고 구성하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-104">To create and configure an **Azure HDInsight Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="33ee1-105">**SSIS 연결 관리자 추가** 대화 상자에서 **AzureHDInsight**를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-105">In the **Add SSIS Connection Manager** dialog box, select **AzureHDInsight**, and click **Add**.</span></span>
2. <span data-ttu-id="33ee1-106">**Azure HDInsight 연결 관리자 편집기** 대화 상자에서 연결할 HDInsight 클러스터에 대한 **클러스터 DNS 이름**(프로토콜 접두사 없이), **사용자 이름** 및 **암호**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-106">In the **Azure HDInsight Connection Manager Editor** dialog box, specify the **Cluster DNS name** (without the protocol prefix), **Username**, and **Password** for the HDInsight cluster to connect to.</span></span>
3. <span data-ttu-id="33ee1-107">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-107">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="33ee1-108">작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ee1-108">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
