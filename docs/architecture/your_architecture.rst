###############################
Architecture for <your product>
###############################

.. package:: <your product>
    :id: P_ID
    :satisfies: [[fetch_elements(filter = "type == 'sw_req'")]]


.. arch_module:: <your module in your product>
   :id: M_ID
   :satisfies: SWRQ_ID
   :implements: IF_ID

   **Element**

   .. needarch::

      rectangle "{{need().title}}" as {{need().id}} {{ref(need().id)}}

   .. instead of explicit manual definition of needarch, we could even use {{flow(need().id)}}
      to achieve the same.


   **Architecture with interfaces**

   .. needarch::
      :key: class

      rectangle "{{need().title}}" as {{need().id}} {{ref(need().id)}}
      {{import("implements")}}
      {% for e in need().implements %}{{e}} <- {{need().id}}
      {% endfor %}
      }


   Implementation:

   .. autosummary::

      merge_dicts


   **Architecture generated from datamodel**

   .. needflow:: Links
      :filter-func: filter.filter_id_linked_element_and_back(M_MERGE_DICTS, implements)
      :link_types: implements
      :show_link_names:
      :align: left

   .. decision:: <Your title here>
      :id: D_M_ID

      <Your implementation evaluation documentation here>



.. if:: <your interface of your product>
   :id: IF_ID
   :satisfies: SWRQ_ID
   :verified_by: TCOVER_ID

   **Architecture**

   .. needarch::

      interface "{{need().title}}" as {{need().id}} {{ref(need().id, text = "")}}

   .. instead of explicit manual definition of needarch, we could even use `{{flow(need().id)}}`
      to achieve the same.

   Implementation: :py:func:`merge_dicts.merge_dicts`

   .. decision:: <Your title here>
      :id: D_IF_ID

      <Your implementation evaluation documentation here>




